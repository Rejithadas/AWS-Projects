
# Mini AWS Cloud Project 

## Project #1: End to End AWS Data Engineering Project Beginner level

### Step #1: Download the Dataset
- Download the  "Superstore" sales dataset from Kaggle.

### Step #1: Store the Dataset in Amazon S3
- Create an S3 bucket named "storeanalysis"
- Within the bucket, create a folder named "orders" to store the sales data.
- Inside "orders," create subfolders based on year (e.g., "year=2017"). 
- This partitioning help in efficient querying.

### Step #2: Load Initial Data:
- Filter the dataset for a specific year and load as incremental data
- Save the filtered data as a CSV file (e.g., "orders_2017.csv").
- Upload "orders_2017.csv" to the relevant subfolder in S3

### Step #3: AWS Glue Crawler and Data Catalog:

- Create a Glue Database
- Create a crawler "orders_project".
- Select the S3 data source (the "orders" folder).
- Configure crawler behavior, choose "Crawl new folders only" (since the data is added  incrementally).
- Set the IAM role to the "AWSGlueServiceRole" or create a new one with appropriate S3 permissions.
- Select the Glue database created.
- Set the frequency to "Run on demand".
- Run the crawlerand it  will scan the S3 folders and files and create tables in the Glue Data Catalog, representing S3 data structure.

### Step #4: Load Incremental Data:
- Prepare Incremental Data for next year and load the same into  the sub folder and re run the crawler rule .
- The crawler will discover the new folder and update the data catalog.

5. Querying with Athena:
- In Athena settings, specify the S3 folder where the SQL query results should be stored.
- Query the "orders" table in the Glue Data Catalog.
- Take advantage of partitions for faster queries.
- More visualisations can be designed using amzon Quicksight.

## Project #2: Visualize Data using Amazon QuickSight (Beginner level)

This project utilizes Amazon S3 and Amazon QuickSight to explore consumer complaint data submitted to the Consumer Financial Protection Bureau (CFPB) against Bank of America from 2017 to 2023. 

Recommended Analysis
- Do consumer complaints show any seasonal patterns?
- Which products present the most complaints? What are its most common issues?
- How are complaints typically resolved?
- Can you learn anything from the complaints with untimely responses?

### Step #1: Store the Dataset in Amazon S3
- Open the Amazon S3 console and click "Create Bucket."
- Name the bucket (e.g., "boafinancial") and keep the settings as default.
- Upload the CSV file and the "manifest.json" file into the bucket.
- Replace the URL in the "manifest.json" file with the S3 URL of your dataset.

### Step #2: Connect S3 Bucket with Amazon Quicksight
- Open the AWS management console and navigate to Amazon Quicksight.
- Select the Amazon S3 bucket created to analyse the data.
- Enter the link to "manifest.json" file and connect to Quicksight.
- Select "interactive sheet" to start creating visualizations.

### Step #4: Create Visualizations
- Drag fields into the graph to create visualizations.
- Sort, filter, and customize the graphs as desired.
- Experiment with different types of graphs like bar charts, tables, etc.

