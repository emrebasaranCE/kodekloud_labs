## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/14](#exercise-114)
- [Exercise 2/14](#exercise-214)
- [Exercise 3/14](#exercise-314)
- [Exercise 4/14](#exercise-414)
- [Exercise 5/14](#exercise-514)
- [Exercise 6/14](#exercise-614)
- [Exercise 7/14](#exercise-714)
- [Exercise 8/14](#exercise-814)
- [Exercise 9/14](#exercise-914)
- [Exercise 10/14](#exercise-1014)
- [Exercise 11/14](#exercise-1114)
- [Exercise 12/14](#exercise-1214)
- [Exercise 13/14](#exercise-1314)
- [Exercise 14/14](#exercise-1414)


##  Introduction

Understanding Terraform.

### Exercise 1/14
In this lab, we will work on configuration directories that have been created under /root/terraform-projects/S3-Buckets.
```bash
OK
```
### Exercise 2/14
Let's first inspect the `configuration files` in the directory called `MCU`.

What is the `AWS region` configured for use in the provider block? (Assuming we do not pass in additional variables during command execution)
```bash
pwd # /root/terraform-projects/S3-Buckets/MCU

cat terraform.tfvars 
# We can see that its `region = "us-east-1"`

```
### Exercise 3/14
There is a resource block configured in the `main.tf` file in this configuration directory. What is the `resource name` that will be provisioned when we run `terraform apply`?
```json
resource "aws_s3_bucket" "marvel-cinematic-universe" {
  bucket = "mcu-202011121359"
}
```
```bash 
# Its `marvel-cinematic-universe`
```
### Exercise 4/14
What is the current state of this `configuration` directory?
```bash
Resources provisioned.
```
### Exercise 5/14
What is the name of the `s3 bucket` that has been created by this configuration?
```bash
# If we look at the inside of the terraform.tfstate, we can see that its:
# "bucket": "mcu-202011121359",
```
### Exercise 6/14
What is the DNS domain name that is created for this bucket?
```bash
# If we run this code, we can gets this outputs:
# 
terraform show  | grep domain 

# bucket_domain_name          = "mcu-202011121359.s3.amazonaws.com"
# bucket_regional_domain_name = "mcu-202011121359.s3.amazonaws.com"
```
### Exercise 7/14
Now, let's move on and work on a different configuration directory called `DC`.
```bash
# OK

cd /root/terraform-projects/S3-Buckets/DC
```
### Exercise 8/14
The `main.tf` file is empty. Use it to create a new S3 with the following specifications:
resource name: `dc_bucket`
bucket name: `dc_is_better_than_marvel`


Once the resource block is complete, run a `terraform init, plan and apply` to try and create the bucket.


If unsure, refer to the documentation. The documentation tab is available at the top right panel.

(it's ok if you get an error! Move on to the next question!)
```bash
# Lets create the resource like this:

resource "aws_s3_bucket" "dc_bucket"{
    bucket="dc_is_better_than_marvel"
}

terraform init
terraform plan
terraform apply

```
### Exercise 9/14
Why did the `terraform apply` command fail?
```bash
# Because Bucket Name was invalid!
```
### Exercise 10/14
That's right! The `bucket name` we used does not conform to a DNS Name standard as it uses `underscores`.
```bash
OK
```
### Exercise 11 /14
Let's fix that now and change the bucket name so that it uses `dashes (-)` instead of `underscore(_)`.

resource name: `dc_bucket`
bucket name: `dc-is-better-than-marvel`


Once the resource block is complete, run a `terraform init, plan and apply` to try and create the bucket.
```bash
terraform init
terraform plan
terraform apply

# Now its created.
```
### Exercise 12/14
Let's move on to the next configuration directory called Pixar.
Same as the directory called DC, we have the `provider.tf`, `variables.tf`, `terraform.tfvars` and an empty `main.tf` file that is already created.

Change directory to Pixar and move on to the next question.
```bash
OK
```
### Exercise 13/14
Aws Cli is installed on the host.
```bash
OK
```
### Exercise 14/14
Let's do that now and upload this image to the s3 bucket! Update the `main.tf` file with the following specifications:

Bucket: `pixar-studios-2020`
Key: `woody.jpg`
Source: `/root/woody.jpg`
Use object (resource) Name: `upload`

Once ready, proceed to run `terraform init, plan and apply`.
```bash
# Lets create the resource first:
resource "aws_s3_object" "upload" {
  bucket = "pixar-studios-2020"
  key    = "woody.jpg"
  source = "/root/woody.jpg"
}

# and then
terraform apply # and then we are done!
```