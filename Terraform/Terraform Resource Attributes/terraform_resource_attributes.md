## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/8](#exercise-18)
- [Exercise 2/8](#exercise-28)
- [Exercise 3/8](#exercise-38)
- [Exercise 4/8](#exercise-48)
- [Exercise 5/8](#exercise-58)
- [Exercise 6/8](#exercise-68)
- [Exercise 7/8](#exercise-78)
- [Exercise 8/8](#exercise-88)

##  Introduction

Understanding Terraform. 

### Exercise 1/8
Navigate to the configuration directory /root/terraform-projects/project-chronos and inspect the files created inside.
```
OK
```
### Exercise 2/8
What is the resource_type of the resource that's currently defined in the main.tf file?

If unsure, refer to the documentation. Documentation tab is available at the top right panel.
```
It's "time_static"
```
### Exercise 3/8
As you can see, the resource block is empty. This is because time_static does not need any arguments to be supplied to work.

When applied as it is, terraform creates a logical resource locally (similar to random_pet) with the current time.
```
OK
```
### Exercise 4/8
Which of the following attributes are exported by the time_static resource?

If unsure, refer to the documentation. Documentation tab is available at the top right panel.
```
id
```
### Exercise 5/8
How do we refer to the attribute called id using a reference expression?
```bash
time_static.time_update.id
```
### Exercise 6/8
Now, update the main.tf file and add a new local_file resource called time with the following requirements:

filename: /root/time.txt
content: Time stamp of this file is `<id from time_update resource>`


Use a reference expression and interpolation.

When ready, run terraform init, plan and apply.
```
## file content that wanted from us:

resource "local_file" "time"{
    filename = "/root/time.txt"
    content = "Time stamp of this file is ${time_static.time_update.id}"
 }
 resource "time_static" "time_update" {
}

```
```bash
terraform init
terraform plan
terraform apply
```
### Exercise 7/8
What is the `id` value?
```bash
# We can see it easily with
terraform show
```
### Exercise 8/8
What is the attribute called rfc3339 that is created for the time_static resource called time_update?

Make use of the terraform show command and identify the attribute values.
```bash
# we can use this command to get the information:
terraform show | grep rfc
```