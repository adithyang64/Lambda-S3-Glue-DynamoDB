# Lambda-S3-Glue_DynamoDB

## Project Architecture:

![Lambda-S3-Glue_DynamoDB-Architecture](https://github.com/adithyang64/Lambda-S3-Glue-DynamoDB/assets/67658457/d2cbb554-8268-46a1-9f83-1d8d180041fe)

## Description:

An AWS Event Bridge Service Triggers an AWS Lambda Function that generates a Mock Json Data, which in turn triggers another Lambda Function (which is added as a Destination Layer to the present Lambda Function) to Write the Data to S3. 
A Crawler is created in Glue which on pointing to the Data location in S3 crawls through and stores the meta Data Info (one such namely, the schema of the data) to AWS Athena DB. 

```
mock_data_generator_lambda.py
```
The above Python script is designed to generate mock employee data. and Similary the below Pythn Script, uses the generated mock employee data into the specified S3 location.

```
write_json_data_to_s3.py
```

The Glue Job, which incorporates the Crawler, can be triggered either manually on demand or scheduled to run automatically. To enable this functionality, the trigger for the Glue Job is integrated with the built-in Workflows feature of AWS Glue. This integration ensures a seamless flow of data from the source to the target, ultimately reaching DynamoDB.

In order to accomplish this, the below Python script is utilized to facilitate the transfer of data from S3 to DynamoDB through the Glue Job. 
```
glue_to_dynamodb_ingestion.py
```

## Scope of Improvement

The project can be enhanced by transitioning from a mock data generation approach to utilizing a real-time dataset. This improvement will ensure that the project operates with relevant information, leading to more accurate and valuable results.

[Refer the Link for collection of screenshots captured during the project execution](https://docs.google.com/document/d/1QX4ry7Vg1zIpWTPB_BjGZJ5N4lsH0zFA/edit?usp=drive_link&ouid=102047065766224889946&rtpof=true&sd=true)
