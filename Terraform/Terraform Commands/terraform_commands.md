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

Understanding Terraform

### Exercise 1/11
Which command can be used to create a visual representation of our terraform resources?
```bash
terraform graph
```
### Exercise 2/11
We have created a configuration directory /root/terraform-projects/project-shazam. The configuration file inside will be used to create an RSA type private key and then a certificate signing request or a csr using this key.

However, there is an error with the configuration.

Use the terraform validate command, troubleshoot, and fix the issue.


You don't have to create the resources yet! You only need to fix the errors reported by terraform validate.
```bash
dsa_bits  = 0485 # we have to change this line to
rsa_bits  = 0485 

```
### Exercise 3/11
Great! If you completed the previous question correctly, terraform validate should have passed!
Now run terraform plan and generate a configuration plan.

Did it work?
```
YEs
```
### Exercise 4/11
Now, try creating the resources with a terraform apply.

Did that work?
```
NO!
```
### Exercise 5/11
The terraform apply failed in spite of our validation working! This is because the validate command only carries out a general verification of the configuration. It validated the resource block and the argument syntax but not the values the arguments expect for a specific resource!
```
OK
```
### Exercise 6/11
Inspect the main.tf and fix the issue.


Once done, run terraform plan and then apply to created the resources.
```
We have to resize the bit size to 2048.
```
### Exercise 7/11
Now format the main.tf file into a canonical format.
```bash
terraform fmt
```
### Exercise 8/11
Now, navigate to the directory /root/terraform-projects/project-a. We have already created the resources specified in this configuration.

Fetch details from the state file and identify the value of the filename argument.

Note: Do not rely on the current value in the configuration file.
```bash
terraform show | grep filename
# With this code, we can see this output easily:
# filename = "/root/codes"
```
### Exercise 9/11
In these terraform labs, we have used multiple providers so far. But, what are providers?
```
Plugins
```
### Exercise 10/11
Which one is a valid sub-command of the terraform providers command?
```bash
# if we can use this command:
terraform providers -h

# we can see sub-commands!
```
### Exercise 11/11
A new configuration directory /root/terraform-projects/provider has been created. We have already run the terraform init command.
Now check the provider plugins that have been downloaded from the command line utility (instead of inspecting the .terraform directory). After that choose the correct option.
```bash
terraform providers
```