# 📊 HR Data Pipeline & Attrition Risk Modeling

📖 **[Read the Full Interactive Case Study on My Notion Portfolio]([[Insert your Notion Link Here]](https://whispering-crater-183.notion.site/Project-HR-Data-Automation-Attrition-Risk-Modeling-using-Excel-314e54702f0b80cb9ec1d0ec671cea52?source=copy_link))**

## 🎯 Project Overview
This project focuses on automating HR data preparation and building a predictive logic model entirely within Microsoft Excel. The objective was to clean, consolidate, and analyze fragmented HR datasets and Training Needs Analysis (TNA) survey responses for over 1,100 employees to proactively identify flight risks.

By utilizing advanced text parsing, relational lookup functions, and modular boolean logic, I transformed static, disconnected tables into a dynamic diagnostic dashboard that evaluates employee attrition risk based on multi-variable business constraints.

## 🛠️ Tools & Functions Demonstrated
* **Tool:** Advanced Microsoft Excel
* **Functions:** `XLOOKUP`, `TEXTBEFORE`, `TEXTAFTER`, Nested `IF/AND/OR`, `DATE`, `TRANSPOSE`
* **Concepts:** ETL (Extract, Transform, Load), Relational Data Integration, Modular Boolean Logic, Feature Engineering, Absolute/Mixed Cell Referencing.

---

## 🧠 Technical Execution & Methodology

### 1. ETL: Text Manipulation & Feature Extraction
To determine branch assignments without manual data entry, I engineered text extraction formulas to dynamically parse the target "Company" branch directly from unstructured employee email addresses.
```text
// Logical Formula
=TEXTBEFORE(TEXTAFTER([Email_Address], "@"), ".")

// Executed Formula
=TEXTBEFORE(TEXTAFTER(B3, "@"), ".")
