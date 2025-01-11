

# Data Catalogue with AWS Glue Crawler

Valtara is a data analytics company that stores large volumes of raw data in AWS S3
buckets. As the data grows, tracking its structure and location becomes increasingly difficult,
complicating their data processing and analytics tasks. They need an efficient way to catalog and
organize their data to streamline their ETL (Extract, Transform, Load) processes and ensure quick
access to the necessary information.

# AWS-Glue-Crawler

<img width="669" alt="Screenshot 2025-01-10 at 21 54 31" src="https://github.com/user-attachments/assets/e352cb4a-bd41-4419-8e7b-85ee779a1a23" />


# Activity Guide: Organizing and Cataloging Data for Valtara Using AWS S3, Glue, IAM Roles, and Glue Crawler

1. Set Up the AWS Environment
Create an IAM Role for AWS Glue:
Navigate to the IAM Console and create a role with the following policies:
AmazonS3FullAccess: Grants Glue access to read and write data in S3.
AWSGlueServiceRole: Allows Glue to interact with other AWS services.
Attach this role to AWS Glue for execution.

2. Prepare the S3 Buckets
Create an S3 Bucket:
Open the S3 Console and create a bucket (e.g., valtara-raw-data) to store raw data.
Upload Data:
Organize raw data into folders based on use cases or departments (e.g., /sales/, /marketing/).
Upload the data files into the respective folders.

3. Create a Glue Database
Open AWS Glue Console:
Navigate to the AWS Glue Console and select Databases.
Create a Database:
Click Add Database and name it (e.g., valtara_data_catalog).
This database will hold the metadata for the cataloged data.

4. Configure and Run a Glue Crawler
Create the Glue Crawler:
In the Glue Console, select Crawlers and click Add Crawler.
Provide the crawler a name (e.g., valtara-crawler).
Specify Data Source:
Choose S3 as the data source.
Provide the S3 bucket path (e.g., s3://valtara-raw-data/) as the source location.
Set IAM Role:
Assign the IAM role created earlier to the crawler.
Target Database:
Specify the Glue database (e.g., valtara_data_catalog) as the target for metadata storage.
Run the Crawler:
Start the crawler to scan the data and create tables with metadata.

5. Verify Data Catalog
Check Glue Tables:
Once the crawler completes, navigate to the Tables section in the Glue Console.
Verify that the tables are created for each folder and dataset, containing schema details such as column names, data types, and locations.

6. Integrate with ETL Pipelines
Create Glue ETL Jobs:
Use the Glue Console to create ETL jobs referencing the cataloged tables.
Define transformations, such as cleaning or enriching data, using Glue Studio or Python scripts.
Automate ETL Jobs:
Schedule jobs to run periodically or trigger them based on data uploads to the S3 bucket.

7. Optimize and Maintain
Update the Crawler:
Schedule the Glue Crawler to run periodically to keep the catalog updated with new data.
Monitor and Debug:
Use CloudWatch to monitor Glue Crawler and ETL job performance.
Resolve errors or schema inconsistencies promptly.

8. Clean Up Resources
Delete Unused Resources:
Remove Glue crawlers, databases, and tables no longer in use.
Archive or Delete Data:
Use S3 lifecycle policies to archive or delete old data to save costs.
