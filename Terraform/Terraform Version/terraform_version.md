## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/5](#exercise-15)
- [Exercise 2/5](#exercise-25)
- [Exercise 3/5](#exercise-35)
- [Exercise 4/5](#exercise-45)
- [Exercise 5/5](#exercise-55)

##  Introduction

Understanding Terraform.

### Exercise 1/5
Navigate to the directory /root/terraform-projects/omega where we have added a configuration file. Inspect the file and choose the correct version of the provider from the below options:
```
terraform {
  required_providers {
    local = {
      source  = "hashicorp/local"
      version = "1.2.2"
    }
  }
}
```
```bash
1.2.2
```
### Exercise 2/5
Now, change to the directory /root/terraform-projects/rotate. We have already initialized the configuration directory using the terraform init command.
Inspect the rotation.tf file and find out the correct version of the provider plugin that is downloaded.
Choose the correct version from the below options:

You don't have to create the resources!!
```
terraform {
  required_providers {
    google = {
      source  = "hashicorp/google"
      version = "> 3.45.0, !=3.46.0, < 3.48.0"
    }
  }
}
```
```bash
3.47.0
```
### Exercise 3/5
Which one of the below is not a valid version constraint operator?
```bash
==
```
### Exercise 4/5
We have been working on a project called nautilus under the configuration directory /root/terraform-projects/nautilus.
Due to a version mismatch, we don't want to download the aws provider version 3.17.0. Which version constraint can be used to achieve this?

You can try to add the below options in nautilus.tf to verify the correct syntax.
```bash
version = "!=3.17.0" # this is the way.
```
### Exercise 5/5
Now, navigate to the directory /root/terraform-projects/lexicorp where we have added the configuration files. Inspect the file and find out which version of providers will be download.

If unsure, refer to the documentation. Documentation tab is available at the top right panel.
```
terraform {
  required_providers {
    k8s = {
      source  = "hashicorp/kubernetes"
      version = "> 1.12.0, != 1.13.1, < 1.13.3 "
    }

    helm = {
      source  = "hashicorp/helm"
      version = "~> 1.2.0"
    }
  }
}

```
```bash
helm 1.2.4 && kubernetes 1.13.2
```