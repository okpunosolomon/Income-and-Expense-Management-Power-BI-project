# 💼 Income & Expense Management Dashboard (Power BI Project)

## 📊 Executive Summary
**Business Problem:**  
Many organizations track budgets manually or in fragmented spreadsheets, making it difficult to compare income and expense performance across multiple departments and years. This leads to late financial insights, poor cost control, and inefficient allocation of resources.

**Solution:**  
This project introduces an interactive **Power BI dashboard** that integrates Excel-cleaned financial data and Power Query transformations to monitor **Actual vs Budget performance** over a six-year period (2019–2024).  
The dashboard dynamically visualizes **income efficiency, expense variance, and overall financial sustainability** using DAX-driven KPIs and visual indicators.

**Impact in Numbers:**  
- Reduced reporting time from hours to minutes.  
- Achieved 100% visibility of over- and under-spending across five major projects.  
- Enabled proactive budget control through variance alerts and performance KPIs.

**Next Steps:**  
Integrate Power Automate alerts for overspending thresholds and embed dashboard insights into Teams for real-time collaboration.

---

## 🧩 Business Problem
The finance team struggled to consolidate project-level income and expenses into a single view that clearly compared **actuals vs budgets**.  
Data existed in multiple Excel sheets with inconsistent formatting, limiting the ability to evaluate trends, detect overspending, or justify budget reallocations.

The key questions this project aimed to answer were:
1. Are projects staying within their budget limits?  
2. Which years or departments show recurring overspending?  
3. How efficiently is income performing against the budget target?  
4. What trends can inform better forecasting and decision-making?

---

## ⚙️ Methodology
### Data Source and Cleaning  
- Source: *Project_Monthly_Performance_2019_2024.xlsx*  
- Tools: **Microsoft Excel** and **Power BI Power Query**  
- Steps:  
  - Removed duplicates and missing entries.  
  - Standardized numeric and currency formats.  
  - Created calculated fields for income and expense variance.  
  - Normalized month/year dimensions for time-series analysis.  

### Data Transformation  
- Established relationships between **Project_ID**, **Income**, and **Expense** tables.  
- Built **KPI measures** in DAX for performance ratios and variance indicators.  
- Implemented **color-coded SVG visuals** to show real-time budget performance directly inside Power BI tables.

---

## 🧠 Skills & Tools Demonstrated
- **Excel:** Data cleaning, formatting, and initial KPI calculations.  
- **Power BI:**  
  - Data modelling and Power Query transformations.  
  - DAX measures for variance, percentage KPIs, and dynamic visuals.  
  - Interactive filters (Year, Month, Project ID).  
- **Visualization Design:**  
  - Custom SVG charts (donut and bar indicators).  
  - Card KPIs with variance trends.  
  - Color logic:  
    - 🟢 < 95% (on target)  
    - 🟠 = 95% (caution)  
    - 🔴 > 95% (overspend)  

---

## 📈 Results & Business Insights
The dashboard provides clear, actionable insights:
- **Income Performance:** Departments consistently exceeding income budgets (up to +6.9%) were identified as scalable models.  
- **Expense Control:** Expense variances showed significant improvement, with most projects maintaining < 95% of their expense budget.  
- **Trend Analysis:** The 2022 period showed a peak in expense control efficiency and income performance recovery post-2020 downturn.  
- **Transparency:** Each project’s actual vs budget comparison is visible, fostering accountability and faster decision-making.

### Sample Visuals
#### ✅ Executive Dashboard Overview  
*(Actual vs Budget summary view)*  
![Dashboard Preview](visuals/dashboard_preview.png)

#### 📊 Project-Level Performance  
*(Yearly income and expense variance trends)*  
![Key Metrics Screenshot](visuals/key_metrics_screenshot.png)

---

## 🪄 Key DAX Highlights
- **% of Income Budget** → measures how much of the income target was achieved.  
- **% of Expense Budget** → tracks expense utilization against plan.  
- **Variance % with Arrows** → dynamic indicators of financial direction.  
- **SVG Donut and Bar Charts** → enhance KPI visuals directly within Power BI without custom visuals.  

All DAX formulas are documented in the [`/dax-measures`](./dax-measures) folder.

---

## 🚀 Next Steps
- Automate weekly financial alerts using **Power Automate**.  
- Connect Power BI with **SharePoint Lists** for live project budget updates.  
- Expand dashboard scope to include **Profit Margin** and **ROI** metrics.  
- Publish insights to **Power BI Service** for real-time stakeholder collaboration.

---

## 🏁 Summary
This project demonstrates a practical, end-to-end financial performance monitoring solution — from Excel data cleaning to Power BI visualization — built with business impact in mind.  
It combines technical precision with strategic design to help organizations stay agile, informed, and financially accountable.

⭐ *“What gets measured gets improved — and what’s visualized gets understood.”*
