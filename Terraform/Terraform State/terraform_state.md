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
Which location is the terraform state file stored by default?
```
Inside the configuration directory
```
### Exercise 2/12
Which option should we use to disable state?
```
https://developer.hashicorp.com/terraform/language/state

We cannot disable state, terraform needs it!
```
### Exercise 3/12
Which format is the state file stored in by default?
```bash
If we look at any .tfstate file, we can see that its `JSON`.
```
### Exercise 4/12
Which of the following commands does NOT refresh the state?
```
Turns out `terraform init` doesnt use the state file!
```
### Exercise 5/12
What is the name of the state file that is created by default?
```
Its `terraform.tfstate` 
```
### Exercise 6/12
Navigate to the configuration directory /root/terraform-projects/project-flash we have created a few configuration files here. The directory has been initialized and the provider plugins downloaded inside the .terraform directory. However, there is no terraform.tfstate file created. Why is that?
```
because command "terraform apply" is not runned.
```
### Exercise 7/12
Run the terraform show command and identify the id created for the resource called speed_force.
```
At first there is no state.
```
### Exercise 8/12
Now, run terraform apply in this directory.
```bash
terraform apply
```
### Exercise 9/12
Now, check terraform show again. What is the value of id for the resource called speed_force?
```
We can see the value with "terraform output" easily!
```
```bash
# local_file.speed_force:
resource "local_file" "speed_force" {
    content              = "speed-force"
    content_base64sha256 = "+hI5F86aVJG7nQ6K0VEOJHTIhlj5aRLnpODNbyZExtI="
    content_base64sha512 = "COfaah4Goo2T1qerQ8gYg5uR6onGpW1IjlpCtZuOW3UT+MH0rzPSj/LSKTJHHCfYVL0w3Q0B78u8RsRpueUNqg=="
    content_md5          = "b5db1e5be7170beefea11ae7271a06a8"
    content_sha1         = "ebeb8b595c8eb4a6e81cacf244146e742fab2981"
    content_sha256       = "fa123917ce9a5491bb9d0e8ad1510e2474c88658f96912e7a4e0cd6f2644c6d2"
    content_sha512       = "08e7da6a1e06a28d93d6a7ab43c818839b91ea89c6a56d488e5a42b59b8e5b7513f8c1f4af33d28ff2d22932471c27d854bd30dd0d01efcbbc46c469b9e50daa"
    directory_permission = "0777"
    file_permission      = "0777"
    filename             = "/root/speed-force"
    id                   = "ebeb8b595c8eb4a6e81cacf244146e742fab2981" # this one
}
```
### Exercise 10/12
We have just added a new configuration file called aws-infra.tf into this configuration directory and provisioned the resources.

These are AWS resources. Don't worry if they are unfamiliar to you, we will soon be learning about them in the upcoming lectures!
```
OK
```
### Exercise 11/12
Inspect the terraform.tfstate file or run terraform show command.

You will notice that all the attribute details for all the resources created by this configuration is now printed on the screen!


Among them is an EC2 Instance which is created by the resource called dev-server. See if you can find out the private_ip for the instance that was created.
```bash
terraform show | grep private_ip # we can easily find it like this!
```
### Exercise 12/12
We will soon be working with AWS services and deploying resources on AWS with Terraform!
```bash
GREAT!
```