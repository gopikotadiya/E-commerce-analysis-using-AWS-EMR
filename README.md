# E-commerce Data Analysis with AWS EMR and EMR Studio

## Overview

This project involves analyzing e-commerce data using PySpark on an AWS EMR (Elastic MapReduce) cluster. The data analysis is facilitated through an EMR Studio workspace, providing an interactive and collaborative environment for data exploration and processing.

## Setup

### 1. AWS Account

Ensure you have an active AWS account with the necessary permissions to create and manage EMR clusters and EMR Studio.

### 2. Kaggle Dataset

Download the e-commerce dataset from [Kaggle](https://www.kaggle.com/datasets/mkechinov/ecommerce-behavior-data-from-multi-category-store) (replace "dataset-link" with the actual link). This dataset contains the necessary data for your analysis.

### 3. Upload Dataset to S3

Upload the downloaded dataset to an S3 bucket. Replace "your-s3-bucket" and "your-prefix" with your own values.

### 4. Create EMR Cluster

#### a. AWS Management Console

1. Open the [AWS Management Console](https://console.aws.amazon.com/).
2. Navigate to the EMR service.
   - Click on "Clusters" in the left sidebar.
   - Click "Create cluster."
   - Choose "Advanced options."
   - Configure your cluster settings, including the applications to install (Spark, Hadoop, etc.).
   - Click "Create cluster."

#### b. AWS CLI

```
# Replace placeholders with your own values
aws emr create-cluster --name YourClusterName --release-label emr-6.0.0 \
--instance-type m5.xlarge --instance-count 3 \
--applications Name=Spark Name=Hadoop --use-default-roles
```

### 5. Create EMR Studio

#### a. AWS Management Console

1. Open the [AWS Management Console](https://console.aws.amazon.com/).
2. Navigate to the EMR service.
   - Click on "EMR Studio" in the left sidebar.
   - Click "Create Studio."
   - Configure your EMR Studio settings, including linking to the EMR cluster created in the previous step.
   - Click "Create Studio."

#### b. AWS CLI

```
# Replace placeholders with your own values
aws emr create-studio --studio-name YourStudioName --auth-mode SSO \
--default-s3-location s3://your-bucket/your-prefix/ \
--engine-security-group-id your-security-group-id \
--workspace-security-group-id your-security-group-id \
--vpc-id your-vpc-id
```

## Technical Issues and Considerations

### Access Permissions

To execute code in the EMR Studio workspace and on the EMR cluster, ensure that you have the necessary access permissions. This includes permissions to interact with S3 buckets, access EMR resources, and other relevant AWS services. Refer to the AWS Identity and Access Management (IAM) documentation for configuring roles and policies.

### AWS Service Costs

Beware that AWS services, especially EMR clusters, may incur costs. The EMR cluster does not provide free-tier CPUs for server setups, and you will be billed based on the selected instance types and usage. Always monitor your AWS Billing Dashboard to avoid unexpected charges.

## Usage

1. Open the EMR Studio workspace.

2. Navigate to the notebook or create a new one for your analysis.

3. In the notebook, connect to the EMR cluster

4. Import Ecomm_Analysis.ipynb file and attach the pyspark kernel.

5. Before executing the impoterd file cells configure S3 bucket location to see the results.