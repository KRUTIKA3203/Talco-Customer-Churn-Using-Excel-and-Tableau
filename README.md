# 📊 Telco Customer Churn Analysis (Excel + Tableau)

This project focuses on understanding customer churn for a telecom company using **Excel** for data cleaning and feature creation, and **Tableau** for building an interactive dashboard.  
The main goal is to identify why customers leave and which segments are at the highest risk of churn.

---

## 📁 Project Files

| File | Description |
|------|-------------|
| **Telco-Customer-Churn Raw data.csv** | Original uncleaned dataset |
| **Telco-Customer-Churn excel.xlsx** | Cleaned dataset + calculated fields + buckets |
| **Tableau Dashboard.twbx** | Fully interactive churn dashboard |
| **Dashboard Screenshot** | Preview of the Tableau dashboard |

---

## 🧹 Data Cleaning & Preparation (Excel)

The cleaning and transformation process was done entirely in **Excel**, including:

- Handling missing / inconsistent values  
- Formatting categorical fields (Yes/No, service types, contract types)  
- Converting strings to numeric for MonthlyCharges, TotalCharges, Tenure  
- Removing duplicates  
- Creating calculated columns for deeper analysis  

### ✔ Custom Columns Created

#### **1. Tenure Bucket**
Grouped customers into meaningful tenure ranges:

- 0 to 10  
- 11 to 20  
- 21 to 30  
- 31 to 40  
- 41 to 50  
- 51 to 60  
- 61 to 70  
- 71 to 80  

**Formula used:**
=VLOOKUP(F2,$AD$3:$AF$10,3,TRUE)


#### **2. Monthly Charges Bucket**
Categorized customers based on their spending level.

**Formula:**
=VLOOKUP([@MonthlyCharges],$AH$3:$AJ$13,3,TRUE)


#### **3. Churn Risk Score**
A custom scoring model created by combining major churn drivers.

**Formula:**
=IF([@Contract]="Month-to-month",1,0)
+IF([@PaymentMethod]="Electronic check",1,0)
+IF([@TechSupport]="No",1,0)
+IF([@OnlineSecurity]="No",1,0)
+IF([@[Tenure Bucket]]="0 to 10",1,0)
+IF(AND([@MonthlyCharges]>=65,[@MonthlyCharges]<=105),1,0)
+IF([@Partner]="No",1,0)
+IF([@PaperlessBilling]="Yes",1,0)
+IF([@InternetService]="Fiber optic",1,0)
+IF([@DeviceProtection]="No",1,0)
+IF([@SeniorCitizen]=1,1,0)


This score helps identify customers who are **most likely to churn**.

#### **4. Lost Revenue**
=IF([@Churn]="Yes",[@MonthlyCharges],0)

---

## 📊 Pivot Analysis (Excel)

Pivot tables were created to understand churn patterns across:

- Gender  
- Partner vs No Partner  
- Contract Type  
- Payment Method  
- Senior Citizen  
- Multiple Lines  
- Phone Service  
- Internet Service (DSL / Fiber / None)  
- Tech Support  
- Online Security  
- Device Protection  
- Streaming Services  
- Tenure Buckets  
- Monthly Charges Buckets  

These pivots clearly showed which customer groups have the highest churn risk.

---

## 📈 Tableau Dashboard

The Tableau dashboard visualizes:

- Overall Churn Rate  
- Lost Revenue & Expected Savings  
- Monthly Charges vs Churn  
- Churn % by Contract Type  
- Churn vs Tenure  
- Payment Method vs Churn  
- Internet Service vs Churn  
- Tech Support & Security Impact  
- Partner vs No Partner  
- Churn Risk Score  

### 📌 Dashboard Screenshot

### **Landing Page**
![Dashboard](/Dashboard.jpg)


---

## 🔍 Key Insights

- **Month-to-month contract customers churn the most**
- **Electronic Check users have the highest churn**
- **Customers without Tech Support or Online Security leave more frequently**
- **Fiber Optic users churn more than DSL users**
- **Churn is highest in the first 10 months of tenure**
- **High monthly charges (₹65–105) increase churn probability**
- **Senior citizens show higher churn**
- **Customers with partners churn less**

---

## 🧠 What I Learned

- How to clean real-world telecom data in Excel  
- Creating buckets, calculated fields, and scoring models  
- Designing a structured Tableau dashboard  
- Understanding churn factors and customer behavior  
- Converting insights into meaningful visuals  
- End-to-end analysis workflow (Raw Data → Excel → Tableau → Insights)

---

## 👩‍💻 Author

**Krutika Chaudhari**
