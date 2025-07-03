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
Which of the following is not a valid variable type?
```
Item
```
### Exercise 2/10
Which one of the below is not a valid data type in terraform?
```
https://developer.hashicorp.com/terraform/language/expressions/types

We got no "Array" as a variable.
```
### Exercise 3/10
Navigate to the directory /root/terraform-projects/variables. Which type does the variable called `number` belong to?

```
file content:

variable "name" {
     type = string
     default = "Mark"
  
}
variable "number" {
     type = bool
     default = true
  
}
variable "distance" {
     type = number
     default = 5
  
}
variable "jedi" {
     type = map
     default = {
     filename = "/root/first-jedi"
     content = "phanius"
     }
  
}

variable "gender" {
     type = list(string)
     default = ["Male", "Female"]
}
variable "hard_drive" {
     type = map
     default = {
          slow = "HHD"
          fast = "SSD"
     }
}
variable "users" {
     type = set(string)
     default = ["tom", "jerry", "pluto", "daffy", "donald", "jerry", "chip", "dale"]

  
}
```
```bash
Its "bool"
```
### Exercise 4/10
How would you fetch the value of the key called `slow` from the variable called `hard_drive` in a `terraform` configuration?

This variable is defined in the file `variables.tf`.
```
var.hard_drive["slow"]
```
### Exercise 5/10
What is the index of the element called `Female` in the variable called `gender`?
```
1
```
### Exercise 6/10
What is the type of variable called `users`?
```
set(string)
```
### Exercise 7/10
However, this variable has been defined incorrectly! Identify the mistake.
```
duplicate elements
```
### Exercise 8/10
We have now updated the main.tf file in the same directory (/root/terraform-projects/variables) and added some resource blocks.

Inspect them.
```
OK
```
### Exercise 9/10
What is the value for the argument called content used in the resource block for the resource jedi?
```
resource "local_file" "jedi" {
     filename = "/root/first-jedi"
     content = "phanius"
}
```
```
phanius
```
### Exercise 10/10
Now, let's update this resource and add variables instead. Use the default value declared in the variable called `jedi`. 

This variable is a map. For the argument called `content` use the value of the key by the same name.
And, similarly, for the argument called `filename` use the value by the same name.  

When ready, run `terraform init, plan and apply` to create this resource.
```
resource "local_file" "jedi" {
     filename = "/root/first-jedi"
     content = "phanius"
}
```
We have to change this, into this;
```
resource "local_file" "jedi" {
     filename = var.jedi.filename
     content = var.jedi.content
}
```