# IA-incaseofstudy
# 🚲 Cyclistic Bike-Share Case Study
*Google Data Analytics Capstone Project*

## 📌 Scenario
Cyclistic is a bike-share company based in Chicago. Since launching its bike-share program in 2016, the company has grown to a fleet of more than 5,800 bicycles. Cyclistic offers two main types of users: **casual riders** (non-members) and **annual members**. The marketing team wants to understand how casual riders and members use Cyclistic bikes differently — and what strategies could turn casual users into paying members.

This project was developed as part of the [Google Data Analytics Certificate](https://www.coursera.org/professional-certificates/google-data-analytics) and serves as a portfolio piece to demonstrate practical skills in data cleaning, analysis, and storytelling.

---

## 🔍 Guiding Question
**How do annual members and casual riders use Cyclistic bikes differently?**  
**What strategies can encourage casual riders to become annual members?**

---

## 💻 Tools Used
- **R** for data cleaning, analysis, and visualization
- **RStudio** as the development environment
- **tidyverse** and **lubridate** packages
- **R Markdown** for documentation

---

## 🧭 Methodology: The Six-Step Data Analysis Process

1. **Ask**  
   - Business Task: Design marketing strategies aimed at converting casual riders into annual members.
   - Stakeholders: Cyclistic marketing team and executive team.

2. **Prepare**  
   - Source: Publicly available historical trip data from [Divvy](https://divvybikes.com/system-data).
   - Data Period: (e.g. May 2022 – April 2023).
   - Format: `.csv` files.

3. **Process**  
   - Merged 12 monthly datasets into one.
   - Removed missing and duplicate values.
   - Converted date and time fields using `lubridate`.

4. **Analyze**  
   - Compared ride lengths, bike types, and days of the week between members and casual riders.
   - Identified behavior trends (e.g., longer rides on weekends by casual users).

5. **Share**  
   - Summary statistics, graphs (bar charts, line plots), and descriptive insights were compiled into this notebook.
   - Recommendations documented below.

6. **Act**  
   - Proposed marketing actions based on insights:
     - Launch weekend promotions.
     - Encourage app use among casual riders.
     - Offer trial memberships.

---

## 📊 Key Findings

- Casual riders tend to ride more on weekends; members ride consistently throughout the week.
- Casual riders take longer rides on average.
- Both user types prefer classic bikes over electric or docked bikes.

---

## 💡 Recommendations

- Create targeted weekend membership campaigns.
- Promote benefits of membership inside the mobile app.
- Offer first-month discounts for casual users.
- Analyze further by surveying casual riders.

---

## ✅ Next Steps

- Create a dashboard using Power BI or Tableau.
- Add advanced insights (e.g., churn prediction or clustering).
- Translate findings into marketing-ready material.

---

## 📁 Folder Structure

```plaintext
cyclistic-case-study/
│
├── data/                # Raw CSV files
├── scripts/             # R scripts used
├── analysis/            # R Markdown and notebooks
├── visuals/             # Charts and graphs
└── README.md            # Project documentation
