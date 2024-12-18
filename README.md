# Spotify End-to-End Data Engineering Project.

### Introduction
 In this project, I have built an ETL(Extract, Transform, Load) pipeline using Spotify API on AWS. The pipeline will retrieve data from Spotify API, transform it to a desired format, and load it into an AWS data store.

 ### Architecture
 ![Architecture](https://github.com/Ebeneer-ebby/spotify-end-to-end-data-pipeline/blob/main/spotify%20imagen.jpg)


### About Dataset/API
This API contains information about music artists, albums, and songs - [Spotify API](https://developer.spotify.com/documentation/web-api)

 ### Services Used
1. **S3 (Simples Storage Service):** Amazon S3 (Simply Storage Service) is a highly scalable object storage service that can store and retrieve any amount of data from anywhere on the web. It is commonly used to store and distribute large media files, data backups, and static website files

2. **AWS Lambda:** AWS Lambda is a serverless computing service that lets you run your code without managing servers. You can use Lambda to run code in response to events like changes in S3, DynamoDB, or other AWS services.

3. **Cloud Watch:** Amazon Cloudwatch is a monitoring service for AWS resources and the applications you run on them. You can use Cloudwatch to collect and track metrics, collect and monitor log files, and set alarms.

4. **Glue Crawler:** AWS Glue Crawler is a fully managed service that automatically crawls your data sources, identifies data formats, and infers schemas to create an AWS Glue Data Catalog.

5. **Data Catalog** AWS Glue Catalog is a fully managed metadata repository that makes it easy to discover and manage data in AWS you can use the Glue Data Catalog with other AWS services, such as Athena.

6. **Amazon Athena:** Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 Using standard SQL. You can use Athena to analyze data in your Glue Data Catalog or in other S3 buckets.

### Install Packages
```
pip install pandas
pip install numpy
pip install spotipy
pip install boto3
```

### Project Execution Flow 
Extract Data from API -> Lambda Trigger (Every day) -> Run Extract Code -> Store Raw Data -> Trigger Transform Function -> Transform Data and Load IT -> Query Using Athena 

The entire data pipeline is designed to be automated and scheduled to run daily. The AWS Lambda Function responsible for data extraction is triggered by Cloud Watch on a daily basis. This ensures that the latest data from the Spotify API is fetched regularly.

Upon successful extraction, the transformation process is triggered automatically for the newly uploaded data. The transformed data is then moved to their respective folders, and the raw data is removed to keep the data clean and organized.

Finally, the data is loaded into Amazon Athena Data Warehouse, providing a centralized and scalable database for performing data analytics and generating insights.

Optionally the data can be exported to any visualization tool in order to create dashboards or EDA looking for new insights and conclusions.
