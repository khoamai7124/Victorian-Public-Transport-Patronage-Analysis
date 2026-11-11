# Victorian Public Transport Patronage Analysis

## 1. Project Overview

This project explores monthly public transport patronage across Victoria from January 2018 to June 2026. The aim was to understand how public transport usage has changed over time, which transport modes account for the largest share of recorded patronage, and how demand has changed from month to month and year to year.

I used Python in Google Colab to work with and inspect the dataset, then Power BI to build an interactive dashboard and communicate the findings.

The project follows an end-to-end analytics process, from preparing the data to identifying patterns and presenting information that could support transport planning and operational decisions.

## 2. Business Questions

The analysis focuses on the following questions:

- How has public transport patronage changed over time?
- Which transport modes account for the largest share of total patronage?
- How does patronage change month to month (MoM)?
- How does patronage compare with the same month in the previous year (YoY)?
- Which months experienced the largest increases or decreases in patronage?
- What should transport planners and operational teams pay attention to when monitoring demand?

## 3. Dataset

The dataset contains monthly public transport patronage figures for six transport modes in Victoria.

**Dataset coverage:** January 2018 – June 2026

**Transport modes included:**
- Metropolitan train
- Metropolitan tram
- Metropolitan bus
- V/Line train
- V/Line coach
- Regional bus

**Data source:** [Insert the original dataset source and link]

The data represents recorded monthly patronage. It does not provide individual passenger-level information or direct measurements of overcrowding, delays or service capacity.

## 4. Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data inspection and preparation |
| Google Colab | Writing and running Python code |
| Pandas | Working with and checking the dataset |
| Power Query | Reshaping and preparing data for reporting |
| Power BI | Data modelling, DAX calculations and dashboard development |
| DAX | Calculating patronage and growth measures |

## 5. Project Workflow

### Step 1: Data Inspection and Preparation – Google Colab

I used Google Colab to work with the dataset before building the dashboard.

The Python notebook covers:
- Importing the dataset and reviewing its structure.
- Inspecting column names, data types and date information.
- Checking for missing values and duplicate records.
- Preparing the data for further analysis.
- Reviewing patronage patterns across the reporting period.

The prepared dataset was then used as the input for the Power BI report.

**Notebook:** [View Google Colab Notebook](INSERT_COLAB_LINK)

### Step 2: Data Transformation – Power Query

After importing the prepared CSV file into Power BI, I used Power Query to reshape the dataset.

The six transport mode columns were converted into two columns:
- `Transport Mode`
- `Patronage`

I also created a `Month Start` date column to support monthly reporting and time-based calculations.

This structure made it easier to compare transport modes and analyse patronage across different months.

### Step 3: Data Modelling and DAX – Power BI

I created a separate Calendar table and connected it to the patronage data through the monthly date column.

I then developed DAX measures to calculate:

- Total Patronage
- Average Monthly Patronage
- Previous Month Patronage
- Month-on-Month (MoM) Change
- MoM Growth (%)
- Previous Year Patronage
- Year-on-Year (YoY) Change
- YoY Growth (%)
- Latest Month Patronage
- Latest Month YoY Growth (%)

These calculations allowed the dashboard to show both overall demand and changes in patronage over time.

### Step 4: Dashboard Development – Power BI

I designed a two-page interactive dashboard.

**Page 1: Executive Overview**

This page provides a high-level summary of public transport patronage, including:
- Total recorded patronage.
- Average monthly patronage.
- Latest month's patronage.
- Latest month's YoY growth.
- Monthly patronage trend.
- Patronage distribution by transport mode.

**Page 2: Demand Trends & Growth Analysis**

This page focuses on changes in demand over time, including:
- Monthly patronage growth (MoM).
- Year-on-year patronage growth (YoY).
- Months with the largest absolute MoM movements.
- Key business insights and management considerations.

The report also includes Year and Transport Mode filters so users can explore different periods and transport categories.

## 6. Key Findings

The analysis produced several notable findings:

**1. Metropolitan train and tram account for most recorded patronage.**

Metropolitan train represented approximately 38.6% of total recorded patronage, followed by metropolitan tram at approximately 32.0%. Metropolitan bus accounted for another 22.4%.

**2. Patronage experienced a substantial decline during 2020.**

The monthly trend shows a sharp reduction in recorded patronage during 2020, followed by a gradual recovery over the following years.

**3. Patronage increased in the first half of 2026.**

Total patronage from January to June 2026 was approximately 8.98% higher than the corresponding period in 2025.

**4. Some months experienced unusually large changes.**

November 2021 recorded an MoM increase of approximately 102.57%, while April 2020 recorded a decrease of approximately 83.33%.

These movements are worth further investigation rather than being automatically treated as errors or evidence of operational problems.

## 7. Business Implications

The findings may help transport planning and operational teams:

- Monitor demand across metropolitan and regional transport modes.
- Identify periods with substantial changes in recorded patronage.
- Compare demand across equivalent reporting periods.
- Use historical trends as a starting point for further service planning and resource allocation analysis.

However, patronage figures alone are not sufficient to determine whether services are overcrowded or whether additional capacity is required. Further information, such as service frequency, passenger distribution and capacity data, would be needed to make those decisions.

## 8. Limitations

There are several limitations to consider:

- The dataset contains aggregated monthly patronage rather than individual passenger journeys.
- It does not include information about service delays, overcrowding, passenger distribution or service capacity.
- Large percentage changes may be influenced by unusually low patronage in the comparison period.
- Data for 2026 only covers January to June, so it should not be compared directly with complete calendar years.

These limitations are important when interpreting the results and considering possible business actions.

## 9. Project Files

The repository is organised as follows:

```text
victorian-public-transport-analysis/
│
├── data/
│   └── public_transport_clean.csv
│
├── notebooks/
│   └── public_transport_analysis.ipynb
│
├── powerbi/
│   └── public_transport_dashboard.pbix
│
├── screenshots/
│   ├── executive_overview.png
│   └── demand_trends_growth.png
│
├── documentation/
│   └── data_dictionary.md
│
└── README.md
```

## 10. Conclusion and Learning Outcomes

This project gave me the opportunity to apply Python, data preparation, data modelling, DAX and Power BI visualisation to a real-world public transport dataset.

Beyond creating charts, I focused on understanding the patterns in the data and presenting the findings in a way that could be understood by non-technical audiences.

Through this project, I strengthened my ability to work through an analytics task from the initial dataset to a final interactive report, while considering the limitations of the data and the business context behind the results.

---

**Author:** [Your Name]

**Tools:** Python | Google Colab | Pandas | Power Query | Power BI | DAX

**Project type:** Business Analytics / Data Analysis
