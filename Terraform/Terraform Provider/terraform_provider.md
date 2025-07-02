## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/12](#exercise-112)
- [Exercise 2/12](#exercise-212)
- [Exercise 3/12](#exercise-312)
- [Exercise 4/12](#exercise-412)
- [Exercise 5/12](#exercise-512)
- [Exercise 6/12](#exercise-612)
- [Exercise 7/12](#exercise-712)
- [Exercise 8/12](#exercise-812)
- [Exercise 9/12](#exercise-912)
- [Exercise 10/12](#exercise-1012)
- [Exercise 11/12](#exercise-1112)
- [Exercise 12/12](#exercise-1212)


##  Introduction

Understanding Terraform.

### Exercise 1/12
We have a new configuration directory located at the path /root/terraform-projects/things-to-do. Inspect this directory and find out the number of providers initialized within this directory.

Do not run terraform init yet!
```tf
resource "local_file" "things-to-do" {
  filename     = "/root/things-to-do.txt"
  content  = "Clean my room before Christmas\nComplete the CKA Certification!"
}
resource "local_file" "more-things-to-do" {
  filename     = "/root/more-things-to-do.txt"
  content  = "Learn how to play Astronomia on the guitar!"
}
```
```
We got none.
```
### Exercise 2/12
How about now? How many provider plugins are installed in this configuration directory?
```bash
We can see it inside the 

# terraform-projects/things-to-do/.terraform/providers/registry.terraform.io/hashicorp/local/2.5.3/linux_amd64/terraform-provider-local_v2.5.3_x5
```
### Exercise 3/12
How many configuration files exist in the directory: /root/terraform-projects/things-to-do ?
```
1
```
### Exercise 4/12
How many resources are configured in this configuration directory?

Count all the resource blocks used.
```
2 Resource
```
### Exercise 5/12
What is the version of the plugin for the local provider that has been downloaded for this configuration?
```
Its 2.5.3
```
### Exercise 6/12
Now, go ahead and create these resources using terraform!

Once done, the two files defined inside the resource blocks should be created with the correct file names and content.
```bash
cd /root/terraform-projects/things-to-do
terraform plan
terraform apply
```
### Exercise 7/12
We have created another directory containing configuration files at /root/terraform-projects/christmas-wishlist.

Inspect this configuration directory.
```bash
cd /root/terraform-projects/christmas-wishlist.
ls -la

# OK
```
### Exercise 8/12
How many resources are configured within this configuration directory?

Make sure to check all the .tf files.
```
2 different resource
```
### Exercise 9/12
What is the filename that will be created by the resource called cyberpunk?

```
# file content:

resource "local_file" "cyberpunk" {
  filename     = "/root/cyberpunk2077.txt"
  content  = "All I need for Christmas is Cyberpunk 2077!"
}
```
```
It's "/root/cyberpunk2077.txt"
```
### Exercise 10/12
Create a new configuration file within the same directory called xbox.tf. This file should make use of the same local_file resource type with the below requirements:


Resource Name: xbox  

filename: /root/xbox.txt  

content: Wouldn't mind an XBox either!  

Once the configuration file has been created, use the terraform workflow to create this resource.
```bash
# created file content:


resource "local_file" "xbox" {
  filename     = "/root/xbox.txt"
  content  = "Wouldn't mind an XBox either!"
}

# and then run these commands:

cd /root/terraform-projects/christmas-wishlist.
terraform init
terraform plan
terraform apply
```
### Exercise 11/12
Now, navigate to the directory /root/terraform-projects/provider-a. We have downloaded a plugin in this directory. Identify the name and type of provider.

If the configuration files in this directory seem unfamiliar, do not worry, these are covered later in the course.
```bash
cd /root/terraform-projects/provider-a
```
```
# file content:

terraform {
  required_providers {
    linode = {
      source = "linode/linode"
      version = "1.13.3"
    }
  }
}
```
```
# And then we can see that the plugin is this:

# Partner - linode
```
### Exercise 12/12
Now, navigate to the directory /root/terraform-projects/provider-b. We have downloaded a plugin in this directory. Identify the name and type of provider.

If the configuration files in this directory seem unfamiliar, do not worry, these are covered later in the course.
```bash
cd /root/terraform-projects/provider-b

```
```
# file content:

resource "local_file" "xbox" {
  filename     = "/root/xbox.txt"
  content  = "Wouldn't mind an XBox either!"
}
```
```

# And in that file we can see this:

# Community - Ansible
```