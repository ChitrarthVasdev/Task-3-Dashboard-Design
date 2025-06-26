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

#### ➤ Remove Index Column (optional)
- Right-click the index column → Remove

#### ➤ Click Close & Apply to save changes
