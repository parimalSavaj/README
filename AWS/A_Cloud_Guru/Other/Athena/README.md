# AWS Athena

## What is AWS Athena?

AWS Athena is a **serverless query service** that allows you to analyze data stored in **Amazon S3** using **SQL (Structured Query Language)**. It is based on **Presto and Trino** and does not require setting up or managing any servers.

## Key Features:

- **Serverless** – No infrastructure to manage.
- **SQL-based** – Query data using standard SQL.
- **Works with S3** – Reads data directly from Amazon S3.
- **Supports Various Formats** – Works with CSV, JSON, Parquet, ORC, and more.
- **Pay-as-you-go** – You are only charged for the data scanned per query.

## How It Works:

1. **Store Data in Amazon S3** – Upload your structured data to an S3 bucket.
2. **Create a Table in Athena** – Define the schema of your data.
3. **Run SQL Queries** – Use Athena’s query editor or connect with BI tools.

## When to Use AWS Athena:

✅ **Log analysis** – Query logs stored in S3 (CloudTrail, VPC logs, etc.).  
✅ **Data analytics** – Analyze large datasets without a traditional database.  
✅ **Business Intelligence (BI)** – Connect Athena to BI tools like Amazon QuickSight.  
✅ **Ad hoc queries** – Quickly explore data without setting up a database.

## When NOT to Use AWS Athena:

❌ **If you only store images, videos, or documents in S3** (Athena queries structured data, not media files).  
❌ **If you need real-time data processing** (Athena is better for batch analysis).  
❌ **If you have a small dataset** (A traditional database may be more cost-effective).

## Pricing:

- You **pay per query**, based on the amount of data scanned.
- Use **compressed and columnar formats (like Parquet)** to reduce costs.

## Related AWS Services:

- **Amazon S3** – Stores the data Athena queries.
- **AWS Glue** – Helps manage metadata for Athena tables.
- **Amazon QuickSight** – BI tool that integrates with Athena.
- **AWS Lake Formation** – Manages data lakes and access control.

## Conclusion:

AWS Athena is a powerful tool for querying large datasets stored in S3 **without managing a database**. It’s ideal for data analytics, logs, and business intelligence.
