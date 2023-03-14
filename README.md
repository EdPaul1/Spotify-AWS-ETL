# Spotify ETL On AWS
## Architecture

![Untitled Diagram(6) drawio](https://user-images.githubusercontent.com/102229086/224921206-691f63ba-3944-44a0-8e50-5847069360ff.png)

## Technologies
* Spotify Api - Data Source
* Python - Extraction ,Transform & Load
* Cloud - Amazon Web Services
* AWS CloudWatch - Weekly Trigger
* AWS Lambda- Run Python Script For Data Extraction & Data Transformation
* AWS S3- Raw Data & Transfrmed Data Storage
* AWS Glue- Data Catalog
* AWS Athena- Analytics
* AWS Redshift- Data Warehouse
* Tableau- Data Visualization

## Summary of the project
To perform analytics on Spotify Top 50 -Global playlist, A client has requested an ETL to be build and scheduled to run weekely for an year.The Top 50 -Global Playlist contains information on Artist name, Song Title, Plays, Album and Song duration.All these will be extracted using the Spotify API.

- A python Script to extract data is run on AWS Lambda and the raw data stored to an S3 Bucket.
- An object put trigger is added to run the data transformation script on lambda once raw data is loaded to s3.
- The Lambda Script stores the transformed data to a different S3 Bucket on which a Crawler is run on AWS Glue to infer the Schema.
- The schema acts as a guide when creating tables in the database on Redshift Cluster.
- Athena is used to run SQL queries on the data.
- A COPY command is run on Redshift to load the data from the S3 Bucket.
- Lastly Redshift is connected to Tableau for Data Visualization.

## Improvements
To Fully automate the Data Pipeline, A Glue job can be used to periodically load the transformed data into redshift.A trigger can also be used to schedule the job.

## Tableau Dashboard
![Dashboard 1](https://user-images.githubusercontent.com/102229086/224932342-fdc2a22f-48ec-40a6-9acf-6c8e684ac182.png)
