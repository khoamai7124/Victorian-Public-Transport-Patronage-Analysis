# Data Dictionary -- Victorian Public Transport Patronage

This document describes the source dataset and the fields created for
the Power BI analysis. It is intended to help readers understand what
each field represents, how the data is structured, and how the main
reporting measures are calculated.

## 1. Dataset Overview

  -----------------------------------------------------------------------
  Item                                Description
  ----------------------------------- -----------------------------------
  Dataset                             Victorian monthly public transport
                                      patronage

  Reporting period                    January 2018 -- June 2026

  Source file                         `public_transport_clean.csv`

  Source format                       CSV

  Original structure                  One row per month, with a separate
                                      column for each transport mode

  Rows in source file                 102

  Columns in source file              10

  Transport modes                     6

  Power BI fact-table rows after      612
  unpivoting                          
  -----------------------------------------------------------------------

The source file contains monthly patronage figures for six transport
modes. In Power BI, these six mode columns are unpivoted into a
`Transport Mode` column and a `Patronage` column. This creates a
long-format table that is easier to filter, compare and visualise.

## 2. Source Dataset Fields

The following fields are present in `public_transport_clean.csv`.

  -----------------------------------------------------------------------------------
  Field                  Data type      Description    Example /      Notes
                                                       format         
  ---------------------- -------------- -------------- -------------- ---------------
  `_id`                  Integer        Identifier for `1`, `2`, `3`  Used to
                                        the source                    identify rows
                                        record.                       in the source
                                                                      file. Removed
                                                                      from the Power
                                                                      BI analysis
                                                                      table because
                                                                      it is not an
                                                                      analytical
                                                                      field.

  `Year`                 Integer        Calendar year  `2018`         Ranges from
                                        associated                    2018 to 2026.
                                        with the                      
                                        monthly                       
                                        record.                       

  `Month`                Integer        Numeric month  `1` = January; Values range
                                        associated     `12` =         from 1 to 12.
                                        with the       December       
                                        record.                       

  `Month name`           Text           Name of the    `January`      Descriptive
                                        month.                        month label
                                                                      corresponding
                                                                      to `Month`.

  `Metropolitan train`   Integer        Monthly        `16,809,932`   Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        metropolitan                  
                                        train                         
                                        services.                     

  `Metropolitan tram`    Integer        Monthly        `15,231,368`   Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        metropolitan                  
                                        tram services.                

  `Metropolitan bus`     Integer        Monthly        `7,568,547`    Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        metropolitan                  
                                        bus services.                 

  `V/Line train`         Integer        Monthly        `1,466,256`    Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        V/Line train                  
                                        services.                     

  `V/Line coach`         Integer        Monthly        `116,568`      Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        V/Line coach                  
                                        services.                     

  `Regional bus`         Integer        Monthly        `721,229`      Source measure;
                                        recorded                      retained as a
                                        patronage for                 numeric count.
                                        regional bus                  
                                        services.                     
  -----------------------------------------------------------------------------------

**Interpretation note:** The source file provides aggregated monthly
patronage figures. It does not contain individual passenger records. The
precise definition of "patronage" and its counting methodology should be
taken from the original data publisher's documentation.

## 3. Power BI Fact Table

The source dataset is transformed in Power Query before being used in
the report.

### Transformation steps

1.  Import `public_transport_clean.csv`.
2.  Unpivot the six transport mode columns.
3.  Rename the unpivoted attribute column to `Transport Mode`.
4.  Rename the unpivoted value column to `Patronage`.
5.  Create `Month Start` using the year and month fields, with the first
    day of each month as the date.
6.  Remove `_id`, as it is not required for the analysis.

After unpivoting, the fact table contains 612 rows: 102 months
multiplied by 6 transport modes.

### Fact table fields

  -----------------------------------------------------------------------------
  Field              Data type         Description       Example
  ------------------ ----------------- ----------------- ----------------------
  `Year`             Whole number      Calendar year of  `2018`
                                       the recorded      
                                       patronage.        

  `Month`            Whole number      Numeric month of  `1`
                                       the recorded      
                                       patronage.        

  `Month name`       Text              Name of the       `January`
                                       month.            

  `Month Start`      Date              Date created from `01/01/2018`
                                       `Year` and        
                                       `Month`, using    
                                       the first day of  
                                       the month.        

  `Transport Mode`   Text              Transport         `Metropolitan train`
                                       category created  
                                       by unpivoting the 
                                       six source mode   
                                       columns.          

  `Patronage`        Whole number      Recorded monthly  `16,809,932`
                                       patronage for the 
                                       relevant          
                                       transport mode.   
  -----------------------------------------------------------------------------

The six possible values in `Transport Mode` are:

-   Metropolitan train
-   Metropolitan tram
-   Metropolitan bus
-   V/Line train
-   V/Line coach
-   Regional bus

## 4. Calendar Table

A separate Calendar table is used for time-based reporting and date
filtering.

  -----------------------------------------------------------------------
  Field                   Data type               Description
  ----------------------- ----------------------- -----------------------
  `Date`                  Date                    Individual calendar
                                                  dates covering the
                                                  reporting period.

  `Month Start`           Date                    First day of the month
                                                  corresponding to each
                                                  calendar date.

  `Year`                  Whole number, if        Calendar year derived
                          created                 from `Date`; can be
                                                  used for year-based
                                                  filtering.
  -----------------------------------------------------------------------

The active relationship connects the Calendar table to the patronage
fact table using the date fields configured in the Power BI model. The
Calendar table supports time-based calculations such as previous-month
and previous-year comparisons.

## 5. DAX Measures

The following measures are used in the Power BI report.

  -------------------------------------------------------------------------------------
  Measure                         Description             Calculation / interpretation
  ------------------------------- ----------------------- -----------------------------
  `Total Patronage`               Total recorded          Sum of `Patronage`.
                                  patronage for the       
                                  current filter context. 

  `Average Monthly Patronage`     Average monthly total   Average of monthly
                                  patronage across the    `Total Patronage`.
                                  months in the current   
                                  filter context.         

  `Previous Month Patronage`      Total patronage for the Uses the previous calendar
                                  month before the        month.
                                  current month.          

  `MoM Change`                    Difference between      Current month minus previous
                                  current-month and       month.
                                  previous-month          
                                  patronage.              

  `MoM Growth (%)`                Percentage change from  `MoM Change` divided by
                                  the previous month.     `Previous Month Patronage`.

  `Previous Year Patronage`       Patronage for the       Uses the same period in the
                                  corresponding period    previous year.
                                  one year earlier.       

  `YoY Change`                    Difference between      Current period minus
                                  current-period and      `Previous Year Patronage`.
                                  previous-year           
                                  patronage.              

  `YoY Growth (%)`                Percentage change       `YoY Change` divided by
                                  compared with the       `Previous Year Patronage`.
                                  corresponding period    
                                  one year earlier.       

  `Latest Month Patronage`        Total patronage for the Evaluates `Total Patronage`
                                  latest month in the     for the latest selected
                                  selected reporting      month.
                                  context.                

  `Latest Month YoY Growth (%)`   Year-on-year growth for Evaluates `YoY Growth (%)`
                                  the latest month in the for the latest selected
                                  selected reporting      month.
                                  context.                

  `Absolute MoM Growth (%)`       Size of the             Absolute value of
                                  month-on-month          `MoM Growth (%)`.
                                  percentage movement,    
                                  regardless of           
                                  direction.              
  -------------------------------------------------------------------------------------

### Calculation notes

-   **MoM** means month-on-month. It compares a month with the
    immediately preceding month.
-   **YoY** means year-on-year. It compares a month with the same month
    in the previous year.
-   Growth measures are formatted as percentages in Power BI.
-   `Absolute MoM Growth (%)` is useful for ranking the largest
    movements, whether they are increases or decreases. It does not show
    the direction of change; use `MoM Growth (%)` for that.
-   The first month in the reporting period has no previous-month
    comparison within the dataset. Similarly, a month without a
    corresponding prior-year period cannot have a YoY comparison.
-   Percentage changes can appear unusually large when the
    comparison-period patronage is very low. They should be interpreted
    alongside the underlying patronage values.

## 6. Data Quality Checks

The source CSV was checked before dashboard development.

  Check                                        Result
  -------------------------------------------- ---------------------------
  Number of source records                     102
  Number of source columns                     10
  Reporting period                             January 2018 -- June 2026
  Unique year-month records                    102
  Missing values in source columns             None found
  Duplicate source rows                        None found
  Missing months within the reporting period   None found
  Unique transport modes after unpivoting      6
  Expected fact-table rows after unpivoting    612

These checks describe the supplied CSV file. They do not independently
verify the accuracy or collection methodology of the original patronage
figures.

## 7. Important Limitations

-   The dataset contains aggregated monthly patronage, not individual
    passenger journeys.
-   It does not include passenger-level locations, service frequency,
    capacity, overcrowding or delay information.
-   The data alone cannot explain why patronage increased or decreased
    in a particular month.
-   The 2026 reporting period ends in June and therefore contains only
    six months of data. It should be compared with January--June in
    previous years rather than complete calendar years.

## 8. Source

**Original dataset:** Monthly public transport patronage by mode

**Dataset URL:** https://opendata.transport.vic.gov.au/dataset/1ab35aa9-f21d-4f00-939b-60dade427d45/resource/07141b34-08f7-430e-bf83-99e9462cc59f/download/monthly_public_transport_patronage_by_mode.csv

Please refer to the original publisher's documentation for the formal
definition of patronage, collection methodology and any revisions to the
data.
