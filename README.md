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





