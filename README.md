# AWS project

This repository is dedicated to showcasing a series of projects focused on **data analysis**, **data quality control**, **diagnostic**, and **data wrangling** using **Amazon Web Services (AWS)**. The goal of this repository is to provide insights into various methodologies for processing and analyzing datasets, building diagnostic dashboards, and ensuring high-quality data for decision-making.

### Key Areas of Focus:
1. **Exploratory Analysis**: Exploring trends in business license data to better understand economic activities in specific regions.
2. **Diagnostic Monitoring**: Leveraging AWS CloudWatch to monitor storage and performance of AWS resources in a data pipeline.
3. **Data Wrangling**: Addressing challenges in cleaning and transforming unstructured datasets for analysis.
4. **Data Quality Control**: Implementing strategies to ensure accuracy and completeness in datasets, particularly for students and registration data.




# Exploratory Data Analysis

### Project Description
Conduct an Exploratory Data Analysis on Business Licenses Data in North Vancouver.

### Project Title
**Understanding Business Trends in North Vancouver**

### Objective
In this project, the main aim is to analyze the business license data of North Vancouver in 2024 through Exploratory Data Analysis. Hence, in this paper, we seek to explore the economic activities of the area of interest by focusing on the business type, the status of the license, and the annual trends. This analysis seeks to answer the following: 

### Architecture
![Descriptive Analysis](https://github.com/user-attachments/assets/bb301928-a8b5-495d-a730-60c75bb0a917)

**In 2024, which business types are most common in North Vancouver, and how are the licenses spread across the different categories?**

### Dataset
The dataset includes detailed information about business licenses issued between 2013 and 2024 across various areas, specifically focusing on North Vancouver. It contains the following key columns:
- **FOLDERYEAR:** Year in which the license was issued (e.g., 24 for 2024).
- **LicenceRSN:** Unique reference number for the license.
- **LicenceNumber:** Unique identifier for the license.
- **LicenceRevisionNumber:** Revision number for the license.
- **BusinessName:** Registered name of the business associated with the license.
- **BusinessTradeName:** Trade name of the business (if applicable).
- **Status:** Current status of the license (e.g., Issued, Gone Out of Business).
- **IssuedDate:** Date when the license was issued, formatted with a timestamp.
- **ExpiredDate:** Expiration date of the license, formatted with a timestamp.
- **BusinessType:** Category of business activity (e.g., Contractor, Computer Services).
- **BusinessSubType:** Subcategory within the business type (e.g., Building, Software).
- **City:** Location of the business associated with the license (e.g., North Vancouver).
- **Province:** Province where the business is located (e.g., BC).
- **Country:** Country where the business is located (e.g., CA for Canada).
- **NumberofEmployees:** Number of employees reported by the business.
- **FeePaid:** License fee paid in Canadian dollars.
- **ExtractDate:** Date when the data was extracted from the source.

### Methodology
1. **Data Collection and Preparation:**  
   a. Load the dataset using S3 by creating different buckets (raw, transform, and curated folders).  
2. **Data Profiling:**  
   a. Used AWS Glue DataBrew to analyze data quality, identify missing values, and assess column distributions.  
3. **Data Cleaning:**  
   a. Cleaned and transformed the data using the following steps:  
      - Removed redundant features, such as Unit and PostalCode.  
      - Filled missing values in fields like `Country` with a default value of "CA" for Canada.  
      - Converted dates to `yyyy-mm-dd` format for uniformity.  
4. **Data Exploration:**  
   a. Compared license issuance trends for 2024, focusing on active and inactive licenses in North Vancouver.  
   b. Summarized licenses by Business Type and analyzed the distribution of statuses.  
5. **Insights and Findings:**  
   a. Identified that "Retail" and "Professional Services" are the most active business categories.  
6. **Conclusion:**  
   Summarized findings suggest that specific industries boost the local economy. This information can be helpful for policy and investment decisions. Future analyses could include projections of license trends.

### Tools and Technologies
- **Amazon S3:** Used to store and organize data in buckets at different stages of the data pipeline (Raw, Transformed, and Curated).
- **AWS Glue DataBrew:** Utilized for data profiling and cleaning, allowing for efficient identification of missing values, outliers, and patterns in the dataset.
- **AWS Glue:** Employed to design and execute the ETL pipeline, transforming raw data into meaningful insights.

### Deliverables
- A detailed report summarizing the methods, findings, and methodology.

---

# Diagnostic Analysis 

### Project Description
AWS CloudWatch in the diagnosis of AWS Resources.

### Project Title
**A Diagnostic Dashboard for AWS Components**

### Objective
This work aims to identify the usage and effectiveness of AWS components used in the data pipeline for business license analysis. The goals include utilizing CloudWatch dashboards to:
- Track storage usage, the number of objects, and the estimated charges for the raw, transformed, and curated buckets.  
- Set alerts to warn when thresholds are crossed, facilitating early intervention.

### Dataset
The diagnostic analysis focuses on AWS resources used in the data pipeline for processing business licenses:
- **S3 Buckets:** Storage and number of objects in each bucket:  
  1. **Raw Bucket:** `ro-rw-irr2`  
  2. **Transformed Bucket:** `to-trf-irr2`  
  3. **Curated Bucket:** `ro-curr-irr2`  
- Projected usage of S3, Glue, and DataBrew for the last 3 months.
- **Alarms Configured:** Alerts for storage limit ranges.

### Methodology
1. **CloudWatch Dashboard Setup:**  
   Developed a dashboard consolidating metrics for S3 buckets and associated AWS components.  
2. **Visualization Components:**  
   a. Line graphs showing storage usage over time.  
   b. Numbers representing the count of objects in each bucket.  
3. **Alerts Dashboard:**  
   Created alarms for bucket storage exceeding defined limits.

### Tools and Technologies
- **AWS CloudWatch:** Used for dashboard visualization and alarm setup.  
- **AWS S3:** Monitored storage usage and object counts.

### Deliverables
- CloudWatch dashboard with interactive visualizations of metrics and alarms.

---

# Data Wrangling 

### Project Description
Exploratory Data Analysis in a Dirty Dataset (Week 3).

### Project Title
**Data Quality: An Exploratory Data Analysis**

### Objective
Identify anomalies, patterns, and insights using features such as age and income. Prepare the dataset for better analysis.

### Dataset
The dataset includes customer information with fields:
- **ID:** Unique customer identifier.  
- **Name:** Customer's full name.  
- **Age:** Customer's age.  
- **Date of Birth:** Birth date in various formats.  
- **Country:** Country of residence.  
- **Income:** Customer's income.  
- **Gender:** Customer's gender.  
- **Transaction Date:** Date of transaction.  
- **Height (cm):** Customer's height in centimeters.  
- **Satisfaction:** Satisfaction level on a scale of 10.

### Methodology
1. **Data Collection and Preparation:**  
   - Ingested raw data into the Amazon S3 Raw Data bucket.  
   - Profiled data using AWS Glue DataBrew.  
2. **Data Cleaning and Transformation:**  
   - Standardized column formats and addressed key data quality issues:
      - Unified country names (e.g., "USA," "United States," "US").
      - Converted income values to a standard currency.  
      - Normalized gender codes ("MALE" to "M").  
      - Imputed missing height values.  
3. **Insights and Findings:**  
   - Highlighted data quality issues, such as negative ages and inconsistent country names.

### Tools and Technologies
- **Amazon S3:** Structured storage of raw, transformed, and curated data.  
- **AWS Glue DataBrew:** For profiling, cleaning, and transformation.

### Deliverables
- Cleaned dataset stored in the Transformed Data bucket on S3.

---

# Data Quality Control 

### Project Description
A review of students, admission, and registration datasets for data quality.

### Project Title
**Improving the Quality of Data**

### Objective
Conduct data quality control to ensure data is accurate, complete, and usable for analysis or operations.

### Background
#### Students Dataset
- Contains student number, name, age, gender, and course of study.  
- **Common issues:** Different gender formats ("Male/M"), inconsistent date formats.

#### Admissions Dataset
- Tracks student applications with fields like admission ID, application date, and admission status.  
- **Common issues:** Blank spaces, inconsistent date formats.

#### Registration Dataset
- Contains course registration records with fields like registration ID and course code.  
- **Common issues:** Blank spaces, inconsistent date formats.

### Methodology
1. **Data Collection and Storage:**  
   - Stored datasets in Amazon S3 buckets:
      - Raw Data Bucket.  
      - Transformed Data Bucket.  
      - Curated Data Bucket.  
2. **Data Profiling:**  
   - Used AWS Glue DataBrew for profiling reports:
      - Standardized gender entries.  
      - Addressed date format inconsistencies.  
3. **Data Cleaning:**  
   - Resolved anomalies and standardized values.  
4. **Data Validation:**  
   - Verified non-null fields like student ID and course code.  
   - Confirmed valid credit values in the registration dataset.  
   - Ensured consistent gender patterns (M/F).

### Tools and Technologies
- **Amazon S3:** For structured storage.  
- **AWS Glue DataBrew:** For profiling, cleaning, and validation.

### Deliverables
- Cleaned datasets stored in the curated bucket on S3.
