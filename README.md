# 🚀 AWS Data Engineering Project

## 📌 Overview

This project demonstrates a simple end-to-end data pipeline using AWS services and Python.
The pipeline uploads data from a local system to Amazon S3 and analyzes it using Amazon Athena with SQL.

---

## 🏗️ Architecture

Local System → Python (boto3) → Amazon S3 → Amazon Athena → SQL Queries

---

## 🛠️ Tech Stack

* AWS S3 (Storage)
* AWS IAM (Access Control)
* AWS Athena (Query Engine)
* Python (boto3)
* SQL
* AWS CLI

---

## ⚙️ Steps Performed

### 1. IAM Setup

* Created IAM user
* Generated Access Key & Secret Key

### 2. AWS CLI Configuration

```bash
aws configure
```

### 3. S3 Setup

* Created S3 bucket
* Uploaded dataset (CSV file)

### 4. Data Upload using Python

```python
import boto3

s3 = boto3.client('s3')
s3.upload_file('cleaned_sales.csv', 'your-bucket-name', 'cleaned_sales.csv')
```

### 5. Athena Setup

* Created database
* Created external table pointing to S3

```sql
CREATE EXTERNAL TABLE sales (
    order_id STRING,
    product STRING,
    amount INT,
    country STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
LOCATION 's3://your-bucket-name/';
```

### 6. Data Analysis using SQL

```sql
SELECT * FROM sales;

SELECT COUNT(*) FROM sales;

SELECT product, SUM(amount)
FROM sales
GROUP BY product;
```

---

## 📊 Output

* Successfully queried data from S3 using Athena
* Generated insights like total sales and product performance

---

## 🎯 Key Learnings

* Built a basic data pipeline using AWS
* Learned IAM security and permissions
* Used Python (boto3) for automation
* Queried data using Athena and SQL
* Debugged real-world issues (permissions, file paths)

---

## 🚀 Future Improvements

* Add ETL pipeline using AWS Glue
* Automate workflow using Airflow
* Build dashboard using Power BI / QuickSight

---

## 📌 Author

Vishnu Priya



This project was built as part of learning Data Engineering concepts and AWS cloud services.
