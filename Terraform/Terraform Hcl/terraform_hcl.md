## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/18](#exercise-118)
- [Exercise 2/18](#exercise-218)
- [Exercise 3/18](#exercise-318)
- [Exercise 4/18](#exercise-418)
- [Exercise 5/18](#exercise-518)
- [Exercise 6/18](#exercise-618)
- [Exercise 7/18](#exercise-718)
- [Exercise 8/18](#exercise-818)
- [Exercise 9/18](#exercise-918)
- [Exercise 10/18](#exercise-1018)
- [Exercise 11/18](#exercise-1118)
- [Exercise 12/18](#exercise-1218)
- [Exercise 13/18](#exercise-1318)
- [Exercise 14/18](#exercise-1418)
- [Exercise 15/18](#exercise-1518)
- [Exercise 16/18](#exercise-1618)
- [Exercise 17/18](#exercise-1718)
- [Exercise 18/18](#exercise-1818)


##  Introduction

Understanding Terraform.

### Exercise 1/18
Welcome to the very first Terraform Lab!

In this lab, we will learn how to get started with HashiCorp Configuration Language that is used by Terraform.
```
Hi
```
### Exercise 2/18
Navigate to the directory /root/terraform-projects/HCL. There is a file present in this location.
What is the file extension used by this file?

List the file by using the ls command.
```
It's ".tf"
```
### Exercise 3/18
That's right! That is a TF file and is used for writing configuration files in Terraform using HCL.
```
Okey!
```
### Exercise 4/18
What is the resource type specified in this file?

From the terminal, inspect it using tools like cat or text editors such as VI .
Alternatively, you can open this file on VS Code. So navigate to this directory and inspect the file.
```tf
<!-- This is the file content -->

resource "local_file" "games" {
  file     = "/root/favorite-games"
  content  = "FIFA 21"
}
```
```
Resource type is: "local_file"
```
### Exercise 5/18
What is the resource name used for the local_file resource in this configuration file?
```
Its called "games"
```
### Exercise 6/18
What is the name of the provider for which we are creating this resource?
```
It's "local".
```
### Exercise 7/18
Which one of the below is not an example of an argument used within the resource block?
```bash
resource_type="local_file"
```
### Exercise 8/18
If you run a terraform plan now? Would it work?
```
Nope, it didn't
```
### Exercise 9/18
Run a terraform init inside the configuration directory: /root/terraform-projects/HCL
```bash
cd /root/terraform-projects/HCL
terraform init # and done!
```
### Exercise 10/18
What was the version of the local provider plugin that was downloaded?
```bash
2.5.3
```
### Exercise 11/18
If you run a terraform plan now? Would it work?
```
No, it didn't work again.
```
### Exercise 12/18
Why did the command fail?

Inspect the error produced when the command was run.

If unsure, refer to the documentation. The documentation tab is available at the top right.
```
Invalid Argument

# this line is the problem;
file = "/root/favorite-games"

# but we have to write it like this:
filename = "/root/favorite-games"
```
### Exercise 13/18
Which of the following is not a valid argument for the local_file resource?

If unsure, refer to the documentation.
```
we got "content", "sensitive_content", "filename" and "file_permission" but not
"file"
```
### Exercise 14/18
Fix the argument in the configuration file and then run a terraform plan followed by terraform apply to create the local_file resource called games.
```bash
terraform init
terraform apply 
```
### Exercise 15/18
We have now created our very first resource using Terraform! Next, let's work on updating the resource.

If you look at the output produced by the terraform plan and terraform apply commands closely, we can see that the file content is printed on the screen.

Since we do not want this to happen, we have updated the resource type.

What is the resource type that we have updated?
```tf
# updated file content:

resource "local_sensitive_file" "games" {
  filename     = "/root/favorite-games"
  content  = "FIFA 21"
  sensitive_content = "FIFA 21"
}
```
```
local_sensitive_file
```
### Exercise 16/18
That's right, we have made use of the local_sensitive_file resource type to mask the contents of the file from the execution plan.

However, something is wrong. If we run terraform plan or terraform apply now we see an error!

Identify and fix the issue.
Remember, we don't want the content of the file to show up in the execution plan at all.
```
resource "local_sensitive_file" "games" {
  filename     = "/root/favorite-games"
  content  = "FIFA 21"
  sensitive_content = "FIFA 21"
}
```
We have to change this file contents to this:
```tf
resource "local_sensitive_file" "games" {
  content = "FIFA 21"
  filename     = "/root/favorite-games"
}
```
### Exercise 17/18
Notice that the content of the file was not displayed when using local_sensitive_file instead of the local_file resource.

Note: Refer to the documentation to see all the arguments supported by this resource.

Also note that as Terraform follows an immutable infrastructure approach, the file was recreated although the contents are the same.
```
OK
```
### Exercise 18/18
Finally, destroy this resource using terraform destroy.
```bash
terraform destroy
```