# 💼 Income & Expense Management Dashboard (Power BI Project)

## 📊 Executive Summary
**Business Problem:**  
Many organizations still track budgets manually or in fragmented spreadsheets, making it hard to compare income and expenses across departments or financial years. This results in slow insight delivery, cost overruns, and missed opportunities for optimization.

**Solution:**  
This project delivers an **interactive Power BI dashboard** that integrates cleaned Excel data and Power Query transformations to monitor **Actual vs Budget performance** (2019–2024).  
It provides real-time tracking of **income efficiency**, **expense control**, and **variance trends**, powered by DAX-based KPIs and SVG visuals.

**Impact:**  
- Cut manual financial reporting time from hours to minutes.  
- Achieved full visibility of over- and under-spending across five key projects.  
- Enabled proactive budget decisions using automated variance indicators.

---

## 🧩 Business Problem
The finance department needed a single, interactive view to track project-level performance.  
Scattered Excel reports made it difficult to assess:
- Are projects staying within approved budgets?  
- Which departments consistently overspend?  
- How close is actual income to planned targets?  
- What trends can inform more accurate forecasts?

This dashboard centralizes those answers — bridging analytics with financial strategy.

---

## ⚙️ Methodology

### Data Source & Cleaning  
**Dataset:** `Project_Monthly_Performance_2019_2024.xlsx`  
**Tools Used:** Microsoft Excel and Power BI  

Key cleaning steps included:  
- Removing duplicates and null values  
- Standardizing date and numeric formats  
- Creating variance and ratio fields  
- Normalizing project and time dimensions  

### Data Transformation in Power BI  
- Built relationships between **Project_ID**, **Income**, and **Expense** tables  
- Developed **KPI measures** using DAX for performance ratios and variance %  
- Applied **color-coded SVG visuals** for intuitive, dynamic performance indicators  

---

## 🧠 Skills & Tools Demonstrated
- **Excel:** Data cleaning and KPI base calculations  
- **Power BI:**  
  - Data modeling and Power Query transformations  
  - DAX measures for ratios, variance %, and KPIs  
  - Interactive slicers for Year, Month, and Project ID  
- **Visualization Design:**  
  - Custom SVG charts (bar and donut progress visuals)  
  - Card visuals for variance %  
  - Conditional color logic for easy insight recognition  

**Color Logic:**  
🟢 < 95% → On Target | 🟠 = 95% → Caution | 🔴 > 95% → Overspend  

---

## 🧱 Data Model Overview  
*(Relationships between Income, Expense, and Date tables)*  

![Data Model](visuals/Model%20View.png)

---

## 🖥️ Dashboard Overview  
*(Actual vs Budget executive summary view)*  

![Dashboard Overview](visuals/Report%20View.png)

---

## 📈 Key Insights & Visual Highlights

### Income vs Budget Performance
Shows how each project performed against its income target between 2019–2024.  
Green KPIs indicate targets exceeded; red highlights shortfalls.

![Income View](visuals/Screenshot%202025-11-09%20110553.png)

---

### Expense Efficiency & Control
Tracks actual expenses versus budgets with DAX-based variance arrows and custom SVG donuts.  
Helps identify where cost reduction or budget reallocation is needed.

![Expense View](visuals/Screenshot%202025-11-09%20110643.png)

---

### Yearly Project Trends
Displays variance across multiple fiscal years — supporting both short-term and long-term budget planning.

![Trends View](visuals/Screenshot%202025-11-09%20110713.png)

---

### Performance Across Projects
Summarized comparison for all projects, enabling leadership to focus on outliers and replicate high-performing models.

![Project Comparison](visuals/Screenshot%202025-11-09%20110738.png)

---

## 🪄 DAX Highlights  
Some key measures that power this dashboard:

- **% of Income Budget** → Measures how much of the income target was achieved  
- **% of Expense Budget** → Tracks utilization against planned spending  
- **Variance % with Arrows** → Adds direction symbols (▲ / ▼) to clarify trends  
- **SVG Donut & Bar Charts** → Generate visual KPIs directly from DAX logic  

📘 Full documentation available in [`/powerbi-files/README_DAX.md`](./powerbi-files/README_DAX.md)

---

## 🚀 Next Steps
1. Integrate **Power Automate** alerts for variance thresholds.  
2. Link to **SharePoint Lists** for live data refresh.  
3. Extend metrics to include **ROI** and **Profit Margin** analysis.  
4. Deploy via **Power BI Service** for real-time collaboration.

---

## 🏁 Summary
This project demonstrates a complete data-to-decision workflow:  
from **Excel cleaning and Power Query transformation** to **Power BI visualization and automation planning**.  
It combines analytics, design, and storytelling to help organizations monitor and optimize financial performance effectively.

⭐ *“What gets measured gets improved — and what’s visualized gets understood.”*
