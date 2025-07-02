## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/10](#exercise-110)
- [Exercise 2/10](#exercise-210)
- [Exercise 3/10](#exercise-310)
- [Exercise 4/10](#exercise-410)
- [Exercise 5/10](#exercise-510)
- [Exercise 6/10](#exercise-610)
- [Exercise 7/10](#exercise-710)
- [Exercise 8/10](#exercise-810)
- [Exercise 9/10](#exercise-910)
- [Exercise 10/10](#exercise-1010)


##  Introduction

Understanding Terraform.

### Exercise 1/10
Can we use multiple providers in the same configuration directory?
```
YES
```
### Exercise 2/10
We have a new configuration directory located at the path /root/terraform-projects/multi-provider. Inspect this directory and find out the number of providers initialized.

Don't run the terraform init command yet!

```
## File contents:

resource "local_file" "pet_name" {
	    content = "We love pets!"
	    filename = "/root/pets.txt"
}

resource "random_pet" "my-pet" {
	      prefix = "Mrs"
	      separator = "."
	      length = "1"
}
```
```
We got zero providers, just resources.
```
### Exercise 3/10
Now, run the terraform init command and inspect the .terraform/providers directory. Count the number of plugins downloaded.
```bash
cd /root/terraform-projects/multi-provider
terraform init
```
### Exercise 4/10
How many plugins are available now in this configuration directory?
```
We got 2
```
### Exercise 5/10
Now, Navigate to the directory /root/terraform-projects/MPL. Create a new configuration file called pet-name.tf.
This file should make use of the local_file and random_pet resource type with the below requirements:

local_file resource details:

Resource name = "my-pet"  
File name = "/root/pet-name"  
Content = "My pet is called finnegan!!"   

random_pet resource details:  

Resource name = "other-pet"  
Length = "1"  
Prefix = "Mr"  
Separator = "."  


Once the configuration file has been created, use the terraform workflow to create this resource.
```
# Created file content:

resource "local_file" "my-pet" {
	    content = "My pet is called finnegan!!"
	    filename = "/root/pet-name"
}

resource "random_pet" "other-pet" {
	    length = "1"
        prefix = "Mr"
        separator = "."
}
```
```bash
# And then run these commands:

cd /root/terraform-projects/MPL
terraform init
terraform plan 
terraform apply
```
### Exercise 6/10
Now change into the directory /root/terraform-projects/provider and inspect the file cloud-provider.tf.
What is the instance_type configured with the resource type called aws_instance?

Don't worry if you are not familiar with the aws providers. We will cover it later on.

```
resource "aws_instance" "ec2_instance" {
	  ami       =  "ami-0eda277a0b884c5ab" 
	  instance_type = "t2.large"
}

resource "aws_ebs_volume" "ec2_volume" {
	  availability_zone = "eu-west-1"
	  size  =    10
}
```
```bash
cd /root/terraform-projects/provider

# We can see that its "t2.large"
```
### Exercise 7/10
What is the name of the resource configured with the resource type kubernetes_namespace in kube.tf file within the same directory?

```
resource "local_file" "data" {
	filename = "/root/k8s.txt"
	content = "kubernetes the hard way!"
}
resource "kubernetes_namespace" "dev" {
  metadata {
    name = "development"
  }
}
```
```
Its "dev"
```
### Exercise 8/10
Let's get some more practice! Now navigate to the directory path /root/terraform-projects/provider-a. Create a configuration file called code.tf.

Using the local_file resource type, write the resource block with the below requirements into the file:

Resource name = iac_code  
File name = /opt/practice 
Content = Setting up infrastructure as code  

When ready, only run the terraform init command, we will run the terraform apply command later on.
```bash
cd /root/terraform-projects/provider-a
```
```
# Created file content:

resource "local_file" "iac_code" {
	filename = "/opt/practice"
	content = "Setting up infrastructure as code"
}
```
```bash
cd /root/terraform-projects/provider-a
terraform init
```
### Exercise 9/10
We have made some changes to the configuration file. Are you able to run terraform apply command?
```
# Edited file content:

resource "local_file" "iac_code" {
	  filename = "/opt/practice"
	  content = "Setting up infrastructure as code"
}

resource "random_string" "iac_random" {
  length = 10
  min_upper = 5
}
```
```
No, I cannot.
```
### Exercise 10/10
This is because whenever we add a resource for a provider that has not been used so far in the configuration directory, we have to initialize the directory by running terraform init command.

Let's do that now. Run terraform init followed by terraform apply command.
```bash
terraform init
terraform apply
```