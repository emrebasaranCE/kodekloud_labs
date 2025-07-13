## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/9](#exercise-19)
- [Exercise 2/9](#exercise-29)
- [Exercise 3/9](#exercise-39)
- [Exercise 4/9](#exercise-49)
- [Exercise 5/9](#exercise-59)
- [Exercise 6/9](#exercise-69)
- [Exercise 7/9](#exercise-79)
- [Exercise 8/9](#exercise-89)
- [Exercise 9/9](#exercise-99)

##  Introduction

Understanding Terraform.

### Exercise 1/9
Navigate to the directory called /root/terraform-projects/data. We have used the configuration files created in this directory to create some resources. Inspect them.
```bash
cd /root/terraform-projects/data
```
### Exercise 2/9
Which provider is used by the configuration files in this directory?
```
We can easily see that its 'random'
```
### Exercise 3/9
Which two resource types are configured in the configuration files?
```
resource "random_uuid" "id1" {
   
}
resource "random_uuid" "id2" {
   
}
resource "random_uuid" "id3" {
   
}
resource "random_uuid" "id4" {
   
}
resource "random_uuid" "id5" {
   
}
resource "random_uuid" "id6" {
   
}
resource "random_uuid" "id7" {
   
}
resource "random_integer" "order1" {
  min     = 1
  max     = 99999
 
}
resource "random_integer" "order2" {
  min     = 1
  max     = 222222
 
}
```
```
Its "random_uuid && andom_integer"
```
### Exercise 4/9
We also defined a few output variables in the output.tf file in this configuration directory. Inspect them.
```
OK
```
### Exercise 5/9
What is the value of the output variable called id2 ?

Use the terraform output command.
```bash
$ terraform output
id1 = "5cfb5dd7-e6da-2d02-4bad-c88fc9fc73fa"
id2 = "aa34908a-2024-3a93-8cdd-03c260464764" # this one
id3 = "b0da1f7f-0317-8f0d-c164-4185f4cba292"
id4 = "55ef4b97-1eee-f039-12ee-82f3895a8b33"
id5 = "0bd77949-be9a-7022-099f-8657f7773fcb"
id6 = "97f72911-d86c-4064-2211-e31f7e52ada7"
id7 = "02c83b63-61c7-8929-6630-535c6e8c5bc6"
order1 = 72186
order2 = 72186
```
### Exercise 6/9
What is the value of the output variable called order1 ?

Use the terraform output command.
```bash
$ terraform output
id1 = "5cfb5dd7-e6da-2d02-4bad-c88fc9fc73fa"
id2 = "aa34908a-2024-3a93-8cdd-03c260464764" 
id3 = "b0da1f7f-0317-8f0d-c164-4185f4cba292"
id4 = "55ef4b97-1eee-f039-12ee-82f3895a8b33"
id5 = "0bd77949-be9a-7022-099f-8657f7773fcb"
id6 = "97f72911-d86c-4064-2211-e31f7e52ada7"
id7 = "02c83b63-61c7-8929-6630-535c6e8c5bc6"
order1 = 72186 # this one
order2 = 72186
```
### Exercise 7/9
We have a new configuration directory located at the path /root/terraform-projects/output. Inspect the configuration files that are created in this directory.

What is the value of the output variable pet-name ?

Use the terraform output command within the new configuration directory.
```bash
cd /root/terraform-projects/output
terraform init
terraform plan
terraform apply -auto-approve
```
### Exercise 8/9
What is the `pet-name` output?
```
it was hornet
```
### Exercise 9/9
We have just updated the main.tf file in this directory with a new resource block.
Add a new output variable with the following specifications:

Output Variable Name: welcome_message  
Value: content of the resource called welcome

When ready, run terraform init, plan and apply
```
output "welcome_message" {
	value = local_file.welcome.content
}
```
```bash
terraform init
terraform plan
terraform apply
```