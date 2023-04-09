# AWS CLI/SDK

## AWS Command Line Interface (CLI)
automate AWS services via scripts

can use CLI perform actions to:
- list buckets, upload data s3
- launch stop start and termiante EC2 instances
- Update security gRoups, ceeat subnets
- switch AWS CLI flag using --profile
- Change --output between json, table and text

`aws s3api list-buckets --output text --profile exampro`

## AWS SDK
SDK allows you to control AWS services using prgorammging languges
set of tools and libraities that you can used to create applications for a specific software packages

AWS SKD set of API libraries that let you integate AWS services into your applciatons

C++
Go
Java
Javascript
.NET
NodeJs
PHP
Python
Ruby


## Using Programmatic Access for AWS Users
Set up Programmatic Access
sets up a .csv file Access file
"AWS Credentials" = "Access Key ID" and "Secret Access Key"
Need to store credentials in user's home eg `~/.aws/credentials`

Credentials files allow you to manage multiple credentials (called profiles)

## Using Cloud9 and CLI Setup
