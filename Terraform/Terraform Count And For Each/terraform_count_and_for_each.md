## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/11](#exercise-111)
- [Exercise 2/11](#exercise-211)
- [Exercise 3/11](#exercise-311)
- [Exercise 4/11](#exercise-411)
- [Exercise 5/11](#exercise-511)
- [Exercise 6/11](#exercise-611)
- [Exercise 7/11](#exercise-711)
- [Exercise 8/11](#exercise-811)
- [Exercise 9/11](#exercise-911)
- [Exercise 10/11](#exercise-1011)
- [Exercise 11/11](#exercise-1111)

##  Introduction

Understanding Terraform.

### Exercise 1/11
A new configuration directory has been created at /root/terraform-projects/project-shade. Inspect it. How many files will be created by this configuration?
```
resource "local_sensitive_file" "name" {
    filename = "/root/user-data"
    content = "password: S3cr3tP@ssw0rd"

}
```
```
1
```
### Exercise 2/11
Now add a `count` argument to create `3` instances of this resource.

When ready, run `terraform init, plan and apply`
```
# we just added `count=3` line 

resource "local_sensitive_file" "name" {
    count = 3
    filename = "/root/user-data"
    content = "password: S3cr3tP@ssw0rd"
}
```
### Exercise 3/11
The resource local_sensitive_file.name is now created as:
```
Since we created count, its `list`
```
### Exercise 4/11
What is the id for the resource element at index 1?
```bash
terraform show
```
### Exercise 5/11
How many files were actually created when apply was run?
```bash
It created 1 file
```
### Exercise 6/11
We have now created a `variables.tf` file in the same configuration directory. Update the `main.tf` file to make use of the list type variable defined for the `filename` argument.


Use count to loop through all the elements of this list and do not use hard-coded values.


Use the variable called `content` for the argument called `content`.
```
We have to create the script like this:

resource "local_sensitive_file" "name" {
    filename = var.users[count.index]
    content = var.content
    count = length(var.users)
}
```
### Exercise 7/11
We have reverted back to the old configuration file and cleaned up the resources created so far.
A variable called users now has default values added to it.

What type of `variable` is it?
```
variable "users" {
    type = list(string)
    default = [ "/root/user10", "/root/user11", "/root/user11", "/root/user10"]
}
variable "content" {
    default = "password: S3cr3tP@ssw0rd"
  
}
```
```
list(string)
```
### Exercise 8/11
Can the same elements in this list be used as it is for a `set` instead?
```
No - There are duplicate elements!
```
### Exercise 9/11
Let's do the same exercise as before but this time we will make use of the `for_each` meta argument to create the files in this configuration.


Just like before don't use any hard-coded values.

Use `for_each` to loop through the list type variable called `users`.

Use the variable called `content` as the value of the argument `content` within main.tf.


When ready, run `terraform init, plan and apply`.
```
# updated file content:

resource "local_sensitive_file" "name" {
    filename = each.value
    for_each = toset(var.users)
    content = var.content

}
```
### Exercise 10/11
The resource called name is now created as:
```bash
map
```
### Exercise 11/11
The resource address with the filename - /root/user11 is now represented as:
```bash
local_sensitive_file.name["/root/user11"]
```