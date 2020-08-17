# Automate Bucketing of Streaming Data

  
This repository accompanies the Automate Bucketing of Streaming Data using Amazon Athena and AWS Lambda blogpost. It contains an [AWS Serverless Application Model (AWS SAM)](https://aws.amazon.com/serverless/sam/) template that deploys two AWS Lambda functions; LoadPartiton and Bucketing function.

The [first function](./functions/LoadPartition.py), runs every hour and reads the new folder created under /raw folder and loads this folder as a new partition to the SourceTable. 

The [second function](./functions/LoadPartition.py), runs every hour and copies the data from /raw to /curated using Create Table AS Select (CTAS)  

```bash
├── README.MD <-- This instructions file

├── functions <-- Two lambda functions used to bucket streaming data
```

  

## Requirements

  

* AWS CLI already configured with Administrator permission



  

## Installation Instructions

  

1.  [Create an AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) if you do not already have one and login.

  

2. Clone the repo onto your local development machine using `git clone`.
3.  Install SAM CLI


  
4. From the command line, change directory into v1 or v2 depending on the version required, then run:

```

sam build

sam deploy --guided

```

Follow the prompts in the deploy process to set the stack name, AWS Region and other parameters.

  

## Parameter Details

  

* InputBucketName: the unique name of a new S3 bucket for this application (bucket names must be lowercase only and globally unique across AWS).

  

## How it works

  

* Upload a JSON file (a JSON array ending with .json) to the target S3 bucket.

* After a few seconds you will see the contents imported into a DynamoDB table created by the SAM deploment.

* This process uses on-demand provisioning in DynamoDB.

  

==============================================

  

Copyright 2020 Amazon.com, Inc. or its affiliates. All Rights Reserved.

  

SPDX-License-Identifier: MIT-0