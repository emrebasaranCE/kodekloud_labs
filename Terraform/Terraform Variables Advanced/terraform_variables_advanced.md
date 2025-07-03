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

Understanding Terraform

### Exercise 1/9
How can we use environment variables to pass input variables in terraform scripts?
```
https://spacelift.io/blog/how-to-use-terraform-variables

TF_VAR_[variable_name]
```
### Exercise 2/9
Which method has the highest priority in Variable Definition Precedence?

If unsure, Refer to the documentation. Documentation tab is available at the top right.
```
https://developer.hashicorp.com/terraform/language/values/variables

command line flag of -var or -var-file
```
### Exercise 3/9
Which one of the following commands is a valid way to make use of a custom variable file with the `terraform apply`command?
```bash
terraform apply -var-file variables.tfvars
```
### Exercise 4/9
We have created some files under the directory `/root/terraform-projects/variables`. Inspect it.
```
OK
```
### Exercise 5/9
What will happen if we run `terraform plan` command right now?

Try it.
```
Error
```
### Exercise 6/9
The terraform plan command did not run as there was no reference for the input variable called filename in the configuration files.

Let's fix that now.
```
OK
```
### Exercise 7/9
Declare the variable called `filename` with type `string` in the file `variables.tf`.
Don't have to specify a `default` value.
```
Lets create a file called Variables.tf and paste this into it:

variable "filename" {
  type = string
  
}
```
### Exercise 8/9
If we run `terraform apply` with a `-var` command line flag as shown below, which value would be considered by `terraform`?

`terraform apply -var filename=/root/tennis.txt`
```
/root/tennis.txt
```
### Exercise 9/9
`Terraform` follows a variable definition precedence order to determine the value and
the command line flag of `–var or –var-file` takes the highest priority.
```
OK
```