# 📊 HR Data Pipeline & Attrition Risk Modeling

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

📖 **[Read the Full Interactive Case Study on My Notion Portfolio](https://whispering-crater-183.notion.site/Project-HR-Data-Automation-Attrition-Risk-Modeling-using-Excel-314e54702f0b80cb9ec1d0ec671cea52?source=copy_link)**

## 📌 Project Overview & Business Impact
This project focuses on automating HR data preparation and building a predictive logic model entirely within Microsoft Excel. The objective was to clean, consolidate, and analyze fragmented HR datasets and Training Needs Analysis (TNA) survey responses for over 1,100 employees to proactively identify flight risks.

**Business Value Delivered:**
* **Predictive HR Action:** Transformed raw survey scores into a predictive business tool, allowing stakeholders to instantly identify high-risk employees and intervene before turnover occurs.
* **Process Automation:** Streamlined operations by replacing manual cross-referencing across 1,100+ records with an instant, automated lookup and logic dashboard, drastically reducing the potential for human error.

<div align="center">
  <img width="1579" height="411" alt="image" src="https://github.com/user-attachments/assets/cd50b0db-37fe-4cac-aa85-8e91cd0f012a" />
  </div>

## 🛠️ Tools & Functions Demonstrated
* **Tool:** Advanced Microsoft Excel
* **Functions:** `XLOOKUP`, `TEXTBEFORE`, `TEXTAFTER`, Nested `IF/AND/OR`, `DATE`, `TRANSPOSE`
* **Concepts:** ETL (Extract, Transform, Load), Relational Data Integration, Modular Boolean Logic, Feature Engineering, Absolute/Mixed Cell Referencing.

---

## 🧠 Technical Execution & Methodology

### 1. ETL: Text Manipulation & Feature Extraction
To determine branch assignments without manual data entry, I engineered text extraction formulas to dynamically parse the target "Company" branch directly from unstructured employee email addresses.
```excel
// Executed Formula
=TEXTBEFORE(TEXTAFTER(B3, "@"), ".")
```

### 2. Relational Data Integration (Bridging Tables)
To retrieve necessary demographics for the dashboard, I encountered a schema mismatch: the search input was an Email Address, but the master TNA table only contained Employee IDs. I engineered a nested lookup to dynamically fetch the ID from the Email List and feed it into the outer lookup, successfully bridging two disconnected datasets without redundant helper columns.
```excel
// Executed Formula (Acting as a relational JOIN)
=XLOOKUP(XLOOKUP(C3, email_list!B:B, email_list!A:A), tna_consolidated_data!A:A, tna_consolidated_data!B:B)
```

### 3. Data Normalization & Absolute Referencing
Restructured raw, wide-format HR tables into normalized, transposed datasets. To ensure data integrity, I utilized absolute referencing (`$`) within my arrays, permanently locking the lookup and return columns so the formula strictly targeted the master data without shifting.
```excel
// Executed Formula
=XLOOKUP(C3, tna_consolidated_data!$A:$A, tna_consolidated_data!$D:$D)
```

### 4. Modular Logic & Attrition Risk Modeling
Instead of writing a single convoluted formula, I utilized modular boolean flags to evaluate each business constraint individually. I then aggregated these flags using a nested IF/AND statement to assign a definitive risk tier (Low, Medium, High).

* **The Constraints:** Salary < Median, NPS < 8 or Future Prospect < 8, Company = "gamma", and Tenure is between 2017-2019.

```excel
// 1. Constraint Evaluation (Boolean Flags Example)
=IF(H3<H2, TRUE, FALSE)  // Compensation Risk
=IF(C5<8, TRUE, FALSE)   // Flight Indicator

// 2. Final Risk Aggregation
=IF(AND(F11=FALSE, F12=FALSE, F13=TRUE, F14=TRUE), "Low",
  IF(AND(F11=TRUE, F12=FALSE, F13=TRUE, F14=TRUE), "Medium",
  IF(AND(F11=TRUE, F12=TRUE, F13=TRUE, F14=TRUE), "High", "N/A")))
```

## 📂 Repository Structure
* [📁 /01_Raw_Data & Excel_Model](./01_Raw_Data_&_Excel_Model) - Contains the fragmented HR datasets and unstructured TNA survey responses and the master Excel workbook with automated ETL pipelines and the Attrition Risk Dashboard.

---
*If you are a recruiter or hiring manager, please visit the **[Notion Case Study](https://whispering-crater-183.notion.site/Project-HR-Data-Automation-Attrition-Risk-Modeling-using-Excel-314e54702f0b80cb9ec1d0ec671cea52?source=copy_link)** for a visual walkthrough of the dashboard and a deeper dive into the business context.*
