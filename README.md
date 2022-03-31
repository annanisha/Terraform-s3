# Terraform-s3
Steps to create static website using terraform

## Introduction.

You can use Amazon S3 to host a static website. So, what would be your plan if you wanted to host multiple static website on AWS?. It would be a time consuming stask, if you are going to create each static webiste via AWS console. The relevants of terraform comes here. Terraform is an infrastructure as code tool that lets you build, change, and version cloud and on-prem resources safely and efficiently.

So, lets build a static website using terraform.

## Working of terraform.

Terraform works by making an API call on your behalf to the provider(AWS, GCP, Azure, etc.) you defined. Now to make an API call, it first needs to be authenticated, and that is done with the help of API keys(AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY). To create an IAM user and its corresponding keys, please check this doc: https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html

Now you have to attach an IAM policy for the IWM user you have created. To attach an existing policy to the user, check this doc: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html#add-policies-console

## Prerequisites.

1. Install terraform.

You may go to terraform offical website https://www.terraform.io/downloads , click on AMd64 option under "LINUX BINARY DOWNLOAD", that will dwonalod a terraform.zip file in to your machine.

Unzip the file and move the terraform folder to binary file location "/usr/local/bin/"

You can refer to this article to install terraform on different opertaing systems: https://learn.hashicorp.com/tutorials/terraform/install-cli

2. Verify the installation.

Verify your instllation using command "terraform -version"

3. How to write the terraform code.

Before we start writing our terraform code, we ahve to organize the files.

Terraform module is a set of Terraform configuration files (*.tf) in a directory. The advantage of using modules is reusability.

main.tf: This is our main configuration file where we are going to define our resource definition.

variables.tf: This file is used to define our variables.

outputs.tf: This file contains output definitions for our resources.

NOTE: Filename doesn’t have any special meaning for terraform as long as it ends with .tf extension, but this is a standard naming convention followed in terraform community.

## Steps to configure a static website using terraform.

## Step 1

Create a s3 bucket using terraform.

First you have to create a folder and provider.tf file inside the folder. Providers allow Terraform to interact with cloud providers.
```
provider "aws" {

    region = var.region
    access_key = var.access_key
    secret_key =  var.secret_key

}
```
So, we are going to create a S3 bucket using terrform, we can start writing the resource code in the main.tf file as shown below:

vim main.tf
```
resource "aws_s3_bucket" "mybucket" {

    bucket = "s3.anishababu.tech"
    tags = {

        Name = "mybucket"
        env = "Dev"
    }
  
}
```
Create a variable.tf file to define the variables.

vim variable.tf

```

variable "region" {
  
  default = "ap-south-1"
}

variable "access_key" {
    default =   "your access key here"
}

variable "secret_key" {
    default = "your secret key here"
  
}
```

## Step 2

Initiate terraform using command  "terraform init"

## Step 3 

Evaluates a Terraform configuration to determine the desired state of all the resources it declares using command "terraform plan"


