# 📘 DAX Measures Documentation  
### *Income & Expense Management Dashboard – Power BI Project*  

This document provides a complete overview of all DAX measures used to develop the **Income and Expense Management Dashboard**.  
It combines **core financial calculations** and **advanced SVG-based KPI visuals**, showing how analytical logic and design come together to drive financial insight in Power BI.

---

## 🧭 Overview  

The project evaluates financial performance across multiple projects and years, focusing on:  
- Income and expense tracking  
- Budget adherence  
- Variance analysis  
- Visual performance reporting  

The DAX measures below are organized into four logical categories:  
1. **Base Financial Measures** – foundational calculations for income, expenses, and budgets  
2. **Variance Analysis** – measures for budget deviation and performance tracking  
3. **Performance Ratios** – KPIs showing achievement levels  
4. **Advanced Visuals (SVG)** – dynamic, color-coded visuals that enhance storytelling  

---

## 💼 1. Base Financial Measures  

These form the foundation of all visualizations and analytics in the dashboard.

### 🔹 Income Actual  
Calculates the total actual income within the selected filters.  
```DAX
Income Actual = SUM('Finance_Data'[Income_Actual])
````

### 🔹 Income Budget

Summarizes all budgeted income values for the selected period.

```DAX
Income Budget = SUM('Finance_Data'[Income_Budget])
```

### 🔹 Expense Actual

Sums all recorded expenses for the given filters.

```DAX
Expense Actual = SUM('Finance_Data'[Expense_Actual])
```

### 🔹 Expense Budget

Returns the total planned or approved expenses.

```DAX
Expense Budget = SUM('Finance_Data'[Expense_Budget])
```

These four measures supply the base logic for subsequent performance, ratio, and variance analyses.

---

## 📊 2. Variance and Performance Analysis

Variance measures identify deviations between actual and budgeted performance.

### 🔹 Income Variance

```DAX
Income Variance = [Income Actual] - [Income Budget]
```

Indicates whether actual income exceeded or fell below budget expectations.

### 🔹 Expense Variance

```DAX
Expense Variance = [Expense Actual] - [Expense Budget]
```

Shows the difference between actual and budgeted spending. Positive values indicate overspending.

### 🔹 Expense Variance %

```DAX
Expense Variance % =
DIVIDE([Expense Variance], [Expense Budget], 0)
```

Expresses the variance as a percentage for easier comparison across categories and time frames.

---

### 🔹 Expense Variance Conditional Formatting

Enhances the presentation of the variance metric by adding intuitive trend arrows.

* ▲ = Over budget
* ▼ = Under budget

```DAX
Expense Variance Conditional Formatting =
VAR _variance = [Expense Variance %]
RETURN
FORMAT(_variance, "#.##%") & " " & IF(_variance > 0, "▲", "▼")
```

---

## 💰 3. Budget Achievement KPIs

These measures assess how effectively budgets were achieved or utilized.

### 🔹 % of Income Budget

Shows what percentage of budgeted income was achieved.

```DAX
% of Income Budget = DIVIDE([Income Actual], [Income Budget], 0)
```

### 🔹 % of Expense Budget

Shows what percentage of the expense budget was consumed.

```DAX
% of Expense Budget = DIVIDE([Expense Actual], [Expense Budget], 0)
```

These KPIs power the dashboard’s performance cards and SVG-based visual indicators.

---

## 🧮 4. Advanced Visuals (SVG-Based KPI Measures)

SVG-based DAX allows Power BI to render lightweight, dynamic visuals directly from measures — ideal for performance dashboards.
To display correctly, set each SVG measure’s **Data Category** to *Image URL*.

---

### 🔹 Expense Bar Chart

A horizontal progress bar showing expense utilization versus budget.

* **Green:** Spending < 95% of budget
* **Amber:** Exactly 95%
* **Red:** Over 95%

```DAX
Expense Bar Chart =
VAR ProgressValue = [% of Expense Budget] * 100
VAR BarHeight = 20
VAR BarY = 20

VAR RedColor = "#FF0000"
VAR AmberColor = "#FFA500"
VAR GreenColor = "#13A806"

VAR FinalColor =
    SWITCH(
        TRUE(),
        ProgressValue < 95, GreenColor,
        ProgressValue = 95, AmberColor,
        ProgressValue > 95, RedColor,
        GreenColor
    )

VAR ProgressPercent = DIVIDE(ProgressValue, 100, 0)

RETURN
"data:image/svg+xml;utf8,
<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' preserveAspectRatio='none' width='100%' height='50'>
  <rect x='0' y='" & BarY & "' width='100' height='" & BarHeight & "' fill='#E0E0E0' rx='5' ry='5'/>
  <rect x='0' y='" & BarY & "' width='" & (ProgressPercent * 100) & "' height='" & BarHeight & "' fill='" & FinalColor & "' rx='5' ry='5'/>
  <text x='50%' y='50%' text-anchor='middle' alignment-baseline='middle' font-size='14' font-family='Arial' fill='#444'>
    " & FORMAT(ProgressValue, "0.00") & " %
  </text>
</svg>"
```

**Use Case:**
Displayed within Power BI table or matrix visuals to provide a quick, intuitive indicator of spending progress.

---

### 🔹 Expense Donut Chart

A circular performance gauge that visually tracks the expense budget percentage using animated SVG rendering.

**Logic Summary:**

* Converts `% of Expense Budget` to a circle circumference.
* Applies color logic (Green < 95%, Amber = 95%, Red > 95%).
* Includes smooth CSS animation for progression.

```DAX
Expense Donut Chart =
VAR ProgressValue = [% of Expense Budget] * 100
VAR DisplayValue = MIN(ProgressValue, 100)
VAR Radius = 42
VAR CircumferenceValue = 2 * PI() * Radius
VAR ProgressLength = (DisplayValue / 100) * CircumferenceValue
VAR CenterX = 60
VAR CenterY = 60
VAR BackgroundStrokeWidth = 12
VAR ProgressStrokeWidth = 16

VAR RedColor = "#FF0000"
VAR AmberColor = "#FFA500"
VAR GreenColor = "#13A806"

VAR FinalColor =
    SWITCH(
        TRUE(),
        ProgressValue < 95, GreenColor,
        ProgressValue = 95, AmberColor,
        ProgressValue > 95, RedColor,
        GreenColor
    )

RETURN
"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 120 120' width='260' height='260'>
<style>
@keyframes progress-fill {
  0% { stroke-dashoffset: " & CircumferenceValue & "; stroke: " & RedColor & "; }
  50% { stroke-dashoffset: " & (CircumferenceValue - (CircumferenceValue * 0.5)) & "; stroke: " & AmberColor & "; }
  100% { stroke-dashoffset: " & (CircumferenceValue - ProgressLength) & "; stroke: " & FinalColor & "; }
}
.progress-ring { animation: progress-fill 2s ease-out forwards; }
</style>
<circle cx='" & CenterX & "' cy='" & CenterY & "' r='" & Radius & "' fill='none' stroke='#E0E0E0' stroke-width='" & BackgroundStrokeWidth & "' />
<circle class='progress-ring' cx='" & CenterX & "' cy='" & CenterY & "' r='" & Radius & "' fill='none' stroke='" & FinalColor & "' stroke-width='" & ProgressStrokeWidth & "' stroke-dasharray='" & CircumferenceValue & "' stroke-dashoffset='" & (CircumferenceValue - ProgressLength) & "' />
<text x='50%' y='55%' text-anchor='middle' alignment-baseline='middle' font-size='18' font-family='Arial' fill='#444'>" & FORMAT(ProgressValue, "0.00") & "%</text>
</svg>"
```

**Use Case:**
Serves as a visual centerpiece in KPI cards and summary pages, offering a quick pulse of budget utilization.

---

## 📅 5. Time Intelligence Extensions *(Optional)*

If a Date table is configured, these DAX measures enhance year-over-year and cumulative analysis.

```DAX
YTD Income = TOTALYTD([Income Actual], 'Calendar'[Date])

YTD Expense = TOTALYTD([Expense Actual], 'Calendar'[Date])

YoY Income Growth =
VAR CurrentYear = [Income Actual]
VAR PreviousYear = CALCULATE([Income Actual], DATEADD('Calendar'[Date], -1, YEAR))
RETURN DIVIDE(CurrentYear - PreviousYear, PreviousYear)
```

---

## ⚙️ Implementation Notes

* All measures assume a base dataset named **'Finance_Data'**.
* SVG measures require their **Data Category** set to *Image URL*.
* Adjust color codes (`#FF0000`, `#FFA500`, `#13A806`) or thresholds (95%) to match organizational reporting standards.
* Ensure you create the base measures before using any derived or visual ones.
* Use descriptive display names for KPIs in Power BI for cleaner dashboard visuals.

---

## 🏁 Summary

These DAX measures work together to transform raw financial data into a dynamic, insight-driven Power BI dashboard.
They automate budget monitoring, enable variance detection, and bring visual clarity through custom SVG-based storytelling.

This file represents a complete DAX reference for the *Income and Expense Management Dashboard*, ensuring transparency, reproducibility, and professional-grade documentation.

---

⭐ *“Data alone tells a story, DAX gives it a voice.”*

```
