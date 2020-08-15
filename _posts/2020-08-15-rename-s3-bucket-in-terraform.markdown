---
layout: post
title:  "Rename AWS S3 bucket in terraform"
date:   2020-08-15
author: Mahesh Kumar Kolla
categories: tech
tags:	aws s3 terraform
---

There is no direct way to rename a S3 bucket from console or from terraform.
We have create a new bucket, copy the content and delete the old bucket. 

- #### Create a new bucket
  
  Go to AWS console and create the new bucket manually by copying the bucket settings from old bucket

- #### Sync the buckets

  Run this command to sync the contents of the old bucket to the new bucket
  
  `aws s3 sync s3://old-bucket s3://new-bucket`

- #### Remove the S3 bucket from the terraform state

  Assuming this is your terraform code to create S3 bucket

  ```hcl-terraform
    resource "aws_s3_bucket" "demo_bucket" {
      bucket = "old-bucket"
    }
  ```
  
  Run the following command to remove the above resource from the terraform state.
  This will make terraform to stop tracking this bucket though the resource is present. 
  We will be adding again with the new bucket created.
  
  `terraform state rm aws_s3_bucket.demo_bucket`

- #### Change the bucket name in terraform code  
    
  ```hcl-terraform
    resource "aws_s3_bucket" "demo_bucket" {
      bucket = "new-bucket"  // Change from old-bucket to new-bucket
    }
  ```
  
- #### Import new bucket to the terraform state

  Provide the terraform resource and the bucket name
     
  `terraform import aws_s3_bucket.demo_bucket new-bucket`
  
  This will allow terraform state to track the new bucket and reflect the changes if any

- #### Terraform apply

  `terraform apply`

- #### Delete old bucket 
  
    Verify if all the contents are present in the new bucket and delete the old bucket from the AWS Console.     
