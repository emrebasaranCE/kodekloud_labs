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

Understanding Terraform.

### Exercise 1/9
Which argument should be used to explicitly set dependencies for a resource?
```bash
depends_on

# https://developer.hashicorp.com/terraform/language/meta-arguments/depends_on
```
### Exercise 2/9
Resource A relies on another Resource B but doesn't access any of its attributes in its own arguments. What is this type of dependency called?
```
explicit dependency
```
### Exercise 3/9
How do we make use of implicit dependency?
```
reference expressions

https://dev.to/pwd9000/terraform-understanding-implicit-and-explicit-dependencies-n9l
```
### Exercise 4/9
In the configuration directory /root/terraform-projects/key-generator, create a file called key.tf with the following specifications:  

Resource Type: tls_private_key  
Resource Name: pvtkey  
algorithm: RSA  
rsa_bits: 4096  


When ready, run terraform init, plan and apply.  
If unsure, refer to the documentation.

```
created file content:

resource "tls_private_key" "pvtkey" {
    algorithm = "RSA"
    rsa_bits = "4096"
}
```
```bash
terraform init
terraform plan
terrafrom apply -auto-approve
```
### Exercise 5/9
Resource tls_private_key generates a secure private key and encodes it as PEM. It is a logical resource that lives only in the terraform state.

You can see the details of the resource, including the private key by running the terraform show command.

You can read the documentation for more details. https://registry.terraform.io/providers/hashicorp/tls/latest/docs/resources/private_key
```
OK
```
### Exercise 6/9
Now, let's use the private key created by this resource in another resource of type local file. Update the key.tf file with the requirements:


Resource Name: key_details  
File Name: /root/key.txt  
Content: use a reference expression to use the attribute called private_key_pem of the pvtkey resource.  


When ready, run terraform init, plan and apply.
```
we have to add this resource:

resource "local_file" "key_details" {
    filename = "/root/key.txt"
    content = tls_private_key.pvtkey.private_key_pem
}
```
```bash 
# then run our codes:
terraform init
terraform plan
terrafrom apply -auto-approve
```
### Exercise 7/9
Now destroy these two resources.  
Use terraform destroy.
```bash
terraform destroy
```
### Exercise 8/9
For the next question, navigate to the directory /root/terraform-projects/explicit-dependency.
```
OK
```
### Exercise 9/9
Within this directory, create two local_file type resources in main.tf file. 

Resource 1:  
Resource Name: whale  
File Name: /root/whale  
content: whale


Resource 2:  
Resource Name: krill  
File Name: /root/krill  
content: krill  

Resource called whale should depend on krill but do not use reference expressions.  

When ready, run terraform init, plan and apply.

```bash
cd /root/terraform-projects/explicit-dependency

vi main.tf
```
then paste this information into the main.tf:
```resource "local_file" "whale" {
    filename = "/root/whale"
    content = "whale"
    depends_on = [ local_file.krill ]
}
resource "local_file" "krill" {
    filename = "/root/krill"
    content = "krill"
}
```