# Task-3-Dashboard-Design

# 📊 Product Sales Call Analysis Dashboard – Power BI

This project presents an interactive dashboard built in **Power BI**, analyzing call center performance based on a product sales dataset. It includes metrics like call volume, pick-up rates, agent performance, and product conversion rates.

---

## 📁 Dataset Overview

**Filename**: `Product_Sales.csv`  
**Records**: 9,939  
**Fields**:
- `AgentID`: Unique ID of the agent
- `CallID`: Call identifier
- `CustomerID`: Unique customer ID
- `PickedUp`: Binary (1 = Call answered, 0 = Missed)
- `Duration`: Call duration (in seconds)
- `ProductSold`: Binary (1 = Product sold, 0 = No sale)
- `Agent_Name`: Full name of the agent

---

## 🧰 Tools Used

- Power BI Desktop
- Power Query Editor

---

## 🛠️ Data Preparation Steps in Power BI

### 1. Load the Data
- Open Power BI Desktop
- Go to `Home → Get Data → Text/CSV`
- Select `Product_Sales.csv` and click **Load**

---

### 2. Add Simulated Date Column (`CallDate`)
Since the original dataset had no timestamp, a simulated `CallDate` was added for time-series analysis.

#### ➤ Open Power Query Editor
- Click `Transform Data` from the Home tab

#### ➤ Add Index Column
- Go to `Add Column → Index Column → From 0`

#### ➤ Add Custom Column
- Go to `Add Column → Custom Column`
- Name it `CallDate` and use the following formula:
  
 datetime(2024, 1, 1, 0, 0, 0) + #duration(Number.Mod([Index], 365), 0, 0, 0) 


#### ➤ Format the Column
- Change the CallDate column’s type to Date

#### ➤ Remove Index Column 
- Right-click the index column → Remove

#### ➤ Click Close & Apply to save changes

## NOTE => For more information about these steps refer to the pdf in repository named : Data Preparation.pdf

## AFTER APPLYING THESE STEPS THE REVISED DATASET OVERVIEW :

## 📁 Dataset Overview

**Filename:** `Product_Sales (2).csv`  
**Columns Used:**
- `CallID`: Unique identifier for each call
- `AgentID`, `Agent_Name`: Identifiers for support agents
- `CustomerID`: Unique customer ID
- `PickedUp`: Indicates if the call was answered (1 = Yes, 0 = No)
- `Duration`: Duration of the call in seconds
- `ProductSold`: Whether a product was sold during the call (1 = Yes, 0 = No)
- `CallDate`: Simulated call date used for time-series analysis

---

## 📊 Dashboard Components

| **Component**       | **Description**                                           |
|---------------------|-----------------------------------------------------------|
| **KPI Cards**        | Display `Total Calls`, `PickedUp %`, `Total Products Sold`, `Conversion Rate`, and `Avg Call Duration` |
| **Line Chart**       | Time series of product sales (`CallDate` vs `Products Sold`) |
| **Bar Chart**        | `Agent_Name` vs `Total Products Sold` to show agent performance |
| **Pie/Donut Chart**  | Distribution of `Picked` vs `Missed` calls                |
| **Table**            | Detailed `Agent-wise` performance summary                |

---

## 🛠️ DAX Measures Used

1) Total Calls = COUNT('Product_Sales (2)'[CallID])

2)PickedUp Calls = 
CALCULATE(
    COUNT('Product_Sales (2)'[CallID]),
    FILTER('Product_Sales (2)', 'Product_Sales (2)'[PickedUp] = 1)
)

3) PickedUp % = 
DIVIDE([PickedUp Calls], [Total Calls], 0)

4) Total Products Sold = 
SUM('Product_Sales (2)'[ProductSold])

5) Conversion Rate = 
DIVIDE([Total Products Sold], [PickedUp Calls], 0)

6) Avg Call Duration (mins) = 
AVERAGE('Product_Sales (2)'[Duration]) / 60


## 🧩 Interactivity Features

- **Drill-down**: Enabled in charts for deeper insights
- **Sync Filters**: Maintain consistent filtering across visuals

## 🎨 Design Highlights

- Clean and intuitive layout with consistent color theme (default)
- Title and section headers for clarity
- Visual hierarchy to guide stakeholder attention
- Responsive layout using grid alignment

## 📝 Key Insights

- Majority of calls are picked up, but conversion rate remains below 20%
- Certain agents have high call volume but lower sales performance
- Sales peak in Q4 (October–December)
- Shorter calls (<2 minutes) often result in fewer conversions

## 📦 Deliverables

| File                                  | Description                          |
|---------------------------------------|--------------------------------------|
| Task 3 Dashboard Design.pbix          | Power BI dashboard file              |
| Product_Sales_Dashboard_Summary.pptx   | PowerPoint summary with insights     |
| Product_Sales (2).csv                  | Final enhanced dataset with CallDate |

## NOTE => IF THE .pbix file does not open refer to the TASK 3 Interactive Dashboard.pdf FILE IN REPOSITORY 

## 🧑‍💼 Author

Created by CHITRARTH VASDEV 





