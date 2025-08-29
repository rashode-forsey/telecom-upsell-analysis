# telecom-upsell-analysis
An analysis of a telco dataset, from SQL querying to a Tableau dashboard, recommending a customer retention and modernization strategy.
# Telecom Upsell Opportunity Analysis  

A complete end-to-end analysis of a telecom dataset — from **SQL querying** to a **Tableau dashboard** — recommending a **customer retention and modernization strategy**.  

---

## 📈 Live Dashboard  
👉 [View the Final Interactive Dashboard on Tableau Public](#)  

---

## 🎯 Project Objective  
The goal of this project was to analyze a telecom company’s customer dataset and identify a key segment for a **technology modernization campaign**.  

Specifically:  
- Find **loyal, long-term customers** still on legacy DSL plans.  
- Evaluate their value and stability.  
- Recommend a strategy to **upgrade them to Fiber Optic service** before churn occurs.  

The final deliverable is an interactive Tableau dashboard that highlights this opportunity and provides a **data-driven retention and upsell strategy**.  

---

## 🛠️ Tech Stack  
- **SQL** → Data exploration, cleaning, and segmentation.  
- **Tableau** → Calculated fields, in-depth analysis, and dashboard creation.  

---

## ⚙️ Project Workflow  

### 1. Data Sourcing  
- Dataset: [Telco Customer Churn (Kaggle)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)  
- Format: CSV, loaded into SQLite for querying.  

### 2. SQL Exploration  
- Counted distribution of customers across internet service types.  
- Segmented loyal DSL customers with tenure > 24 months.  

**Example query – Customer distribution by internet service:**  
```sql
SELECT
    InternetService,
    COUNT(customerID) AS TotalCustomers
FROM
    customer
GROUP BY
    InternetService;
```
Example query – Identifying high-tenure DSL customers:
```sql
SELECT
    customerID,
    tenure,
    InternetService
FROM
    customer
WHERE
    InternetService = 'DSL' AND tenure > 24
ORDER BY
    tenure DESC;
```
### 3. Tableau Analysis & Visualization

- Created calculated fields to define the "High Potential Upsell" segment.
- Built dashboard with three main views:
  - Opportunity size (count of DSL customers).
  - Average monthly charges by segment.
  - Treemap of contract distribution.

---
  
### 💡 Key Findings & Recommendation
- Insight: A segment of 1,335 loyal DSL customers is surprisingly high-value, with an average monthly bill of $64.33.
- Strategy: The treemap reveals these customers are highly stable, with the majority locked into one- and two-year contracts. The opportunity lies in proactively migrating them to faster, more capable data plans at the end of their contract cycle to prevent churn to competitors.
- Recommendation: Develop a targeted marketing campaign for "High Potential Upsell" customers whose contracts are expiring in the next 3-6 months. Offer a seamless, promotional upgrade to their plans to promote retention and modernization.

---
### 🚀 Getting Started  

Follow these steps to reproduce the analysis:  

1. **Download the dataset**  
   - Get the [Telco Customer Churn dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).  

2. **Set up the database**  
   - Load the CSV file into a SQLite database (or your SQL engine of choice).  
   - Example with SQLite CLI:  
     ```bash
     sqlite3 telco.db
     .mode csv
     .import WA_Fn-UseC_-Telco-Customer-Churn.csv customer
     ```

3. **Run SQL queries**  
   - Use the provided queries (see [SQL Exploration](#2-sql-exploration)) to segment customers and identify upsell opportunities.  

4. **Open Tableau**  
   - Connect Tableau to your SQLite database or CSV file.  
   - Create calculated fields to define the **High Potential Upsell** segment.
    ```sql
        IF [Internet Service] = "DSL" AND [Tenure] > 24
        THEN "High Potential Upsell"
        ELSE "Standard Account"
        END
    ```  

5. **Explore the dashboard**  
   - Open the Tableau workbook `telecom_upsell_dashboard.twbx`  
   - Or view it directly on Tableau Public: [View Here](https://public.tableau.com/app/profile/rashode.forsey/viz/TelecomUpsellOpportunityAnalysis/AnalysisofUpsellOpportunitiesforPremiumInternet).  
---
### 📊 Final Dashboard  
👉 [View the Tableau Dashboard](https://public.tableau.com/app/profile/rashode.forsey/viz/TelecomUpsellOpportunityAnalysis/AnalysisofUpsellOpportunitiesforPremiumInternet)  
