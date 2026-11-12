# Victorian Public Transport Patronage Analysis

## 1. Project Overview

This project analyses monthly public transport patronage across Victoria from January 2018 to June 2026.

The aim is to understand historical public transport demand, identify changes in patronage across different transport modes, and explore patterns that may be useful for transport planning and operational decision-making.

I approached this project in two stages:

- **Python / Jupyter Notebook (Google Colab):** Used for exploratory data analysis, investigating different analytical questions and understanding patterns in the dataset.
- **Power BI:** Using a clean dataset created from Jupyter Notebook to develop an interactive reporting dashboard that presents selected findings through KPIs, visualisations and business insights.

Although both tools use the same underlying dataset, they serve different purposes. The notebook focuses on exploring the data in greater depth, while the Power BI dashboard focuses on communicating the most relevant information clearly to a business audience.

## 2. Business Context and Analytical Questions

Public transport patronage data can help provide an understanding of how demand changes over time and how usage is distributed across transport modes.

This project explores the following broader questions:

- How has public transport patronage changed over time?
- Which transport modes account for the largest share of recorded patronage?
- Are there noticeable seasonal or historical patterns in demand?
- How has patronage changed compared with previous months and years?
- Which periods experienced unusually large increases or decreases?
- What do these patterns suggest for ongoing demand monitoring?

These questions provide the overall direction of the project. They are explored in more detail in the notebook and translated into a more focused reporting dashboard in Power BI.

## 3. Dataset

The dataset contains monthly public transport patronage figures for six transport modes in Victoria.

**Reporting period:** January 2018 – June 2026

**Transport modes:**
- Metropolitan train
- Metropolitan tram
- Metropolitan bus
- V/Line train
- V/Line coach
- Regional bus

**Data source:** [Monthly public transport patronage by mode](https://opendata.transport.vic.gov.au/dataset/1ab35aa9-f21d-4f00-939b-60dade427d45/resource/07141b34-08f7-430e-bf83-99e9462cc59f/download/monthly_public_transport_patronage_by_mode.csv)

The dataset contains aggregated monthly patronage figures rather than individual passenger-level records.

## 4. Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data inspection, preparation and analysis |
| Google Colab / Jupyter Notebook | Exploratory data analysis and documentation |
| SQL / DuckDB | Querying and analysing structured data, where applicable |
| Power Query | Data transformation in Power BI |
| Power BI | Interactive dashboard development |
| DAX | KPI and time-based calculations |

## 5. Project Workflow

### Part A: Exploratory Data Analysis – Python / Jupyter Notebook

**Purpose: Explore the dataset and investigate analytical questions in greater depth.**

I used Google Colab to inspect, prepare and analyse the dataset before developing the Power BI dashboard.

The notebook focuses on exploratory analysis, including:

- Reviewing the dataset structure, variables and data types.
- Checking data quality and preparing the data for analysis.
- Exploring historical patronage trends.
- Comparing patronage across different transport modes.
- Investigating month-on-month and year-on-year changes.
- Examining recovery patterns compared with 2019.
- Exploring seasonality and variations in demand.
- Identifying periods with unusually large changes in patronage.

The notebook provides a more detailed analytical view of the dataset. It allows different questions and patterns to be investigated without restricting the analysis to the visualisations selected for the final dashboard.

**Notebook:** [Victorian-Public-Transport-Patronage-Analysis.ipynb](https://colab.research.google.com/drive/11rRv1W9oAcKvkMXeEpFyd1CJphF4nZQu?usp=sharing)

### Part B: Interactive Business Reporting – Power BI

**Purpose: Present selected findings in a clear and interactive format for business users.**

After exploring the dataset, I developed a two-page Power BI dashboard to communicate the most relevant performance indicators and demand trends.

Unlike the notebook, the dashboard does not attempt to reproduce every exploratory analysis. Instead, it focuses on information that would be useful for monitoring patronage performance and understanding changes in demand.

**Page 1: Executive Overview**

This page provides a high-level summary of public transport patronage through:

- Total recorded patronage.
- Average monthly patronage.
- Latest month's patronage.
- Latest month's year-on-year growth.
- Monthly patronage trends.
- Patronage distribution across transport modes.

**Page 2: Demand Trends & Growth Analysis**

This page provides a closer look at changes in patronage through:

- Month-on-month (MoM) growth.
- Year-on-year (YoY) growth.
- Months with the largest absolute monthly movements.
- Key business insights.
- Management considerations.

The dashboard also includes Year and Transport Mode filters, allowing users to explore patronage across different reporting periods and transport categories.

### How the Two Components Work Together

The notebook and Power BI dashboard are complementary parts of the same project.

| Aspect | Python / Jupyter Notebook | Power BI |
|---|---|---|
| Main purpose | Explore and investigate the data | Communicate findings |
| Focus | Broader analytical questions | Selected business performance indicators |
| Approach | Detailed, exploratory analysis | Structured, interactive reporting |
| Output | Code, analysis and exploratory visualisations | Two-page interactive dashboard |
| Intended audience | Analysts and technical reviewers | Business users and decision-makers |

The notebook helps develop an understanding of the dataset and identify meaningful patterns. Power BI then turns selected findings into a more accessible reporting format.

The two outputs are not intended to contain identical questions or visualisations. However, they use the same underlying dataset and consistent definitions wherever the same measures are reported.

## 6. Key Findings

The analysis identified several notable patterns:

**1. Metropolitan train and tram account for most recorded patronage.**

Metropolitan train represents approximately 38.6% of total recorded patronage, followed by metropolitan tram at approximately 32.0%. Metropolitan bus accounts for another 22.4%.

**2. Patronage experienced a substantial decline during 2020.**

The historical trend shows a sharp reduction in recorded patronage during 2020, followed by a gradual recovery over subsequent years.

**3. Patronage increased during the first half of 2026.**

Total patronage from January to June 2026 was approximately 8.98% higher than during the corresponding period in 2025.

**4. Some months experienced unusually large changes.**

November 2021 recorded a month-on-month increase of approximately 102.57%, while April 2020 recorded a decrease of approximately 83.33%.

These movements are worth further investigation. They should not automatically be treated as data errors or evidence of operational problems.

## 7. Business Implications

The findings provide several areas that transport planning and operational teams could monitor:

- Track patronage trends across metropolitan and regional transport modes.
- Identify periods with substantial changes in recorded demand.
- Compare performance across equivalent reporting periods.
- Use historical patronage patterns as a starting point for further demand and service planning analysis.

However, monthly patronage figures alone cannot determine whether services are overcrowded or whether additional capacity is required. Further information, such as service frequency, passenger distribution and service capacity, would be needed to support those decisions.

## 8. Data Limitations

Several limitations should be considered when interpreting the results:

- The dataset contains aggregated monthly patronage rather than individual passenger journeys.
- It does not include direct measurements of overcrowding, service delays or passenger distribution.
- Large percentage movements may be influenced by unusually low patronage in the comparison period.
- The 2026 data only covers January to June, so it should not be compared directly with complete calendar years.

These limitations are important when interpreting the findings and considering possible business actions.

## 9. Repository Structure

```text
victorian-public-transport-analysis/
│
├── data/
│   ├── public_transport.csv
│   └── public_transport_clean.csv
│
├── notebooks/
│   └── victorian_public_transport_patronage_analysis.ipynb
│
├── powerbi/
│   └── public_transport_dashboard.pbix
│
├── screenshots/
│   └── dashboard_screenshots.pdf
│
├── documentation/
│   └── data_dictionary.md
│
└── README.md
```

## 10. Conclusion and Learning Outcomes

This project gave me the opportunity to apply data analytics techniques on a real-world public transport dataset, from initial data exploration to interactive business reporting. I used Python and Jupyter Notebook to explore different aspects of patronage and to explore trends beyond the final dashboard. I then used Power BI to select and communicate the relevant findings through performance indicators, trend analysis and business insights. The project enhanced my practical experience in data preparation, exploratory analysis, time-based calculations, data visualisation and communication in business. It also highlighted the need to consider data limitations when translating analytical findings into business recommendations.

---

**Author:** Anh Khoa Mai

**Project area:** Business Analytics | Public Transport | Demand Analysis

**Tools:** Python | Google Colab | Pandas | SQL / DuckDB | Power Query | Power BI | DAX
