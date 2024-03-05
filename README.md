# Video-metrics
## We build a insights dashboard based on "Trending YouTube Video Statistics" dataset available on kaggle.

## We start of by downloading the dataset and setup aws cli on our system.
## 1. Create an S3 bucket and push all these data files seperated as jsons and csv files using the s3-cli-commands file provided.
Amazon S3: Amazon S3 is an object storage service that provides manufacturing scalability, data availability, security, and performance
AWS IAM: This is nothing but identity and access management which enables us to manage access to AWS services and resources securely.

## 2. Now create an aws glue crawler with path to S3 csv files.
AWS Glue: A serverless data integration service that makes it easy to discover, prepare, and combine data for analytics, machine learning, and application development.

## 3. Once the crawler creates a catalog table, view the table using Athena. 
AWS Athena: Athena is an interactive query service for S3 in which there is no need to load data it stays in S3.

## 4. The jsons are not in a proper format hence we use AWS Lambda to handle to json format and create preprocessed json that is useable in Athena.
## For this purpose we create another s3 bucket to hold the new data, in Lambda function create a new function and run the transformation

## 5. Execute the python code in lambda-function.py where we use awswrangler a library that can access the files in s3. This way we create cleaned json to parquet file. Now we create ETL pipeline in glue studio by selecting the parent data catalogs and join. 

<img width="620" alt="Screen Shot 2024-03-04 at 4 54 12 PM" src="https://github.com/SadakhyaNarnur/Video-metrics/assets/111921205/03c28645-16a0-44af-a467-c9678eab87f6">

## 6. Once the data is cleaned and ready it is stored into the s3 bucket. This data is used to make visualization.
