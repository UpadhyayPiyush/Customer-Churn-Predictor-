# Customer Churn Predictor 

## Project Overview 
This project focuses on analyzing telecom customer churn to understand why customers leave and how churn can be reduced using data-driven insights. 
The workflow combines MySQL, Power BI, and Python to deliver an end-to-end analytics and prediction solution. 
Customer data was cleaned and structured through an ETL pipeline, followed by in-depth churn analysis using SQL. 
An interactive Power BI dashboard was developed to visualize churn trends, customer behavior, and revenue impact. 
Additionally, a Random Forest machine learning model was built to predict high-risk churn customers with 84% accuracy. 
The project helps businesses proactively identify churn risk and improve customer retention strategies.


## Business Problem & Objective 
Customer churn is a major challenge for telecom companies, leading to significant revenue loss and reduced customer lifetime value. With increasing competition, retaining existing customers is more cost-effective than acquiring new ones. However, identifying why customers churn and which customers are at risk is not always straightforward.
The objective of this project is to analyze customer behavior, identify key churn drivers, calculate churn metrics (27.4% churn rate), and build a predictive model to proactively detect high-risk churn customers, enabling data-driven retention strategies.


## Schema Structure 
``` sql
#Creating Customer Table
CREATE TABLE customer_data (
    Customer_ID VARCHAR(20),
    Gender VARCHAR(10),
    Age INT,
    Married VARCHAR(10),
    State VARCHAR(50),
    Number_of_Referrals INT,
    Tenure_in_Months INT,
    Value_Deal VARCHAR(20),
    Phone_Service VARCHAR(5),
    Multiple_Lines VARCHAR(10),
    Internet_Service VARCHAR(10),
    Internet_Type VARCHAR(20),
    Online_Security VARCHAR(20),
    Online_Backup VARCHAR(20),
    Device_Protection_Plan VARCHAR(20),
    Premium_Support VARCHAR(20),
    Streaming_TV VARCHAR(20),
    Streaming_Movies VARCHAR(20),
    Streaming_Music VARCHAR(20),
    Unlimited_Data VARCHAR(5),
    Contract VARCHAR(50),
    Paperless_Billing VARCHAR(5),
    Payment_Method VARCHAR(30),
    Monthly_Charge FLOAT,
    Total_Charges FLOAT,
    Total_Refunds FLOAT,
    Total_Extra_Data_Charges INT,
    Total_Long_Distance_Charges FLOAT,
    Total_Revenue FLOAT,
    Customer_Status VARCHAR(20),
    Churn_Category VARCHAR(30),
    Churn_Reason VARCHAR(100)
);

# Creating Views for Churned Customers and New Joined Customers
Create view View_Churndata as
select * from customer_data
where Customer_Status IN ('Churned', 'Stayed');

Create view view_JoinData as
select * from customer_data 
where customer_status = 'Joined';  
```


## Tools & Technologies 
- **MySQL** – Data storage, ETL pipeline, data cleaning, and SQL-based churn analysis  
- **Power BI** – Interactive dashboards, DAX KPIs, slicers, bookmarks, and tooltips  
- **Python** – Data preprocessing, machine learning, and churn prediction  
- **Libraries** – Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Joblib  
- **Machine Learning** – Random Forest Classifier for churn prediction


## Project Workflow 
**ETL (Extract, Transform, Load)**
- Imported raw telecom customer data into MySQL Workbench and designed a structured ETL pipeline.
- Performed data cleaning by handling missing values, removing inconsistencies, and correcting data types.
- Created derived fields such as tenure buckets and standardized categorical values to prepare the dataset for analysis and modeling.

**Analysis** 
- Conducted in-depth exploratory analysis using SQL queries to understand customer behavior and churn patterns.
- Calculated key metrics such as overall churn rate (27.4%), churn by contract type, tenure groups, and internet services.
- Analyzed revenue loss from churned customers to highlight high-impact customer segments.

**Prediction**
- Preprocessed data in Python using Pandas and NumPy, including label encoding of categorical variables and feature selection.
- Split the data into training and testing sets and trained a Random Forest Classifier, achieving 84% accuracy.
- Evaluated model performance using confusion matrix, precision, recall, F1-score, and feature importance to identify key churn drivers.
- Applied the trained model to new customer data to predict high-risk churners.

**Visualization**
- Developed a two-page Power BI report with interactive KPIs, slicers, bookmarks, and tooltips.
- The first page presents an overall churn and customer overview, while the second page focuses on predicted churners and revenue at risk.
- Designed visuals to support business decision-making by clearly highlighting churn trends, risk segments, and actionable insights.


## Key Insights 
- The dataset contains 6,418 total customers, out of which 1,732 customers have churned, resulting in an overall churn rate of ~27%. 
- Month-to-month contracts show the highest churn rate (~46.5%), compared to One-Year (11%) and Two-Year (2.7%) contracts, making contract type a major churn driver. 
- Customers with Fiber Optic internet experience the highest churn (~41.1%), significantly higher than DSL (~19.4%) and Cable (~25.7%) users. 
- The machine learning model identified 378 customers as high-risk churners and achieved an overall prediction accuracy of 84%, enabling proactive churn identification.


## Recommendations
- Prioritize retention efforts for customers on month-to-month contracts, especially those with short tenure (<12 months), as they contribute the highest share of churn.
- Introduce targeted offers or service improvements for Fiber Optic customers, where churn exceeds 40%, to reduce dissatisfaction and switching behavior.
- Use the 378 predicted high-risk churners from the ML model to run focused retention campaigns, such as plan upgrades or loyalty incentives.
- Leverage the Power BI dashboard to continuously monitor churn KPIs (27% churn rate, 1,732 churned customers) and track improvements over time.


## Dashboard & Model Highlights
![Summary Page](https://github.com/UpadhyayPiyush/Customer-Churn-Predictor-/blob/main/Summary.png)
![Prediction Page](https://github.com/UpadhyayPiyush/Customer-Churn-Predictor-/blob/main/Prediction.png)

- Designed a two-page Power BI dashboard featuring an Overview page for overall churn metrics and a Predicted Churners page focused on high-risk customers identified by the ML model.
- Implemented 10+ DAX KPIs including total customers (6,418), churned customers (1,732), and overall churn rate (27.4%).
- Added advanced Power BI features such as slicers, bookmarks, navigation buttons, and custom tooltips to enable interactive exploration.
- Integrated machine learning predictions into Power BI to highlight 378 high-risk churn customers and visualize revenue at risk.
- Visualized key churn drivers such as contract type, tenure, and internet service, enabling stakeholders to identify and prioritize retention actions.
