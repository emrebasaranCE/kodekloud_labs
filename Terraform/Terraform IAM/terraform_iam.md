## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/13](#exercise-113)
- [Exercise 2/13](#exercise-213)
- [Exercise 3/13](#exercise-313)
- [Exercise 4/13](#exercise-413)
- [Exercise 5/13](#exercise-513)
- [Exercise 6/13](#exercise-613)
- [Exercise 7/13](#exercise-713)
- [Exercise 8/13](#exercise-813)
- [Exercise 9/13](#exercise-913)
- [Exercise 10/13](#exercise-1013)
- [Exercise 11/13](#exercise-1113)
- [Exercise 12/13](#exercise-1213)
- [Exercise 13/13](#exercise-1313)


##  Introduction

Understanding Terraform IAM.

### Exercise 1/13
In this lab, we will learn how to deploy AWS resources using `Terraform` with the same mocking service that we use in the `AWS CLI` lab.
```bash
OK
```
### Exercise 2/13
Let's start off by creating an `IAM User` called `mary` but this time by making use of Terraform. In the configuration directory `/root/terraform-projects/IAM`, create a file called `iam-user.tf` with the following specifications:


Resource Type: `aws_iam_user`  
Resource Name: `users`  
Name: `mary`

Once the file has been created, run `terraform init`.
```
# we have to create this resource.
resource "aws_iam_user" "users" {
    name = "mary"
}
```
```bash
terraform init # then run this command.
```
### Exercise 3/13
Great! We now have a configuration file with a simple resource block for creating an IAM User with Terraform!

Let's check if everything is in order for us to create this resource.

Run `terraform plan` within this configuration.

Did that work?
```
No, it didn't worked.
```
### Exercise 4/13
Why did the previous command fail?

Inspect the error message.
```
Planning failed. Terraform encountered an error while generating this plan.

╷
│ Error: Invalid provider configuration
│ 
│ Provider "registry.terraform.io/hashicorp/aws" requires explicit configuration. Add a
│ provider block to the root module and configure the provider's required arguments as
│ described in the provider documentation.
│ 
╵
╷
│ Error: invalid AWS Region: 
│ 
│   with provider["registry.terraform.io/hashicorp/aws"],
│   on <empty> line 0:
│   (source code not available)
│ 
╵
```
```
Region is not set.
```
### Exercise 5/13
Let's do that now. We will add the argument `region` in our provider block called `aws`.

We can do this via other means as well ( like the ones we saw in the lecture).

However, we will be making use of the provider block to define additional arguments to make use of the mocking framework. We will see those in the later questions of this lab.
```bash
OK
```
### Exercise 6/13
Add a new file called `provider.tf` containing a provider block for `aws`.
Inside this block add a single argument called `region` with the value `ca-central-1`


You don't have to run a `terraform plan` or `apply` at this stage.
```
# we have to create this provider:

provider "aws" {
    region = "ca-central-1"
}

```
### Exercise 7/13
Run a `terraform plan` now. Does it work?
```bash
NO
```
### Exercise 8/13
Since we are making use of the mocking framework, the credentials defined using `aws configure` (stored within the file `/root/.aws/credentials`) do not work as it is.

We have now updated the `provider.tf` file with additional arguments to make it work. Take a look.

The `endpoint` argument is similar to the one we saw with the `AWS CLI` where we used the `--endpoint http://aws:4566`. Here we have defined it to make it work with the `IAM` service.


Please note that these additional configurations are not needed when working directly with the AWS Cloud. It is only needed by the lab as it is using an AWS mock framework.
```bash
OK
```
### Exercise 9/13
Now, run a `terraform plan` and then a `terraform apply`
```
It works!
```
### Exercise 10/13
Great! We have added one user called `mary`. However, `project_sapphire` has 5 more people who need access to the `AWS` Account!

Let's use the `count` meta-argument and the new `variables.tf` file created in the configuration directory to create these additional users!

Inspect the newly created `variables.tf` file and answer the subsequent questions.
```
OK
```
### Exercise 11/13
What is the name of the variable that has been added to the `variables.tf` file?
```
variable "project-sapphire-users" {
     type = list(string)
     default = [ "mary", "jack", "jill", "mack", "buzz", "mater"]
}
```
```bash
# project-sapphire-users
```
### Exercise 12/13
What is the data type used for the variable called `project-sapphire-users`?
```bash
# list(string)
```
### Exercise 13/13
Now, update the `iam-user.tf` to make use of the `count` meta-argument to loop through the `project-sapphire-users` variable and create all the users in the list.


You may want to make use of the `length` function to get the length of the list.
```
# newly created iam-user.tf file:

resource "aws_iam_user" "users" {
    for_each = toset(var.project-sapphire-users)
    name = each.value
}

```
```bash
# there was some problem while using count, so i just used for_each
```