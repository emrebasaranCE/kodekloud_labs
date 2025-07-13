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
We have a directory created called /root/terraform-projects/project-mysterio. The main.tf file already has a couple of resource blocks.

Which resource types do they use?
```
resource "local_file" "file" {
    filename = var.filename
    file_permission =  var.permission
    content = random_string.string.id
    
}

resource "random_string" "string" {
    length = var.length
    keepers = {
        length = var.length
    }  
    
}
```
```
We can see that its using both `local_file` and `random_string`
```
### Exercise 2/12
Now, create these two resources that have been defined in this configuration file.
```bash
terraform init
terraform plan
terraform apply
```
### Exercise 3/12
Which resource is created first in this case?
```
Since there is an implicit dependency defined in the file resource, the string is created first.
```
### Exercise 4/12
We have modified the resource configuration again. Run a terraform plan now. What would happen?
```
both resources will be replaced.
```
### Exercise 5/12
Why is the string resource being re-created?
```
The variable that the resource was calling has changed.
```
### Exercise 6/12
All the resources for the random provider can be recreated by using a map type argument called keepers. A change in the value will force the resource to be recreated.


This argument accepts arbitrary key/value pairs and in our example, it is set to the key called length whose value was updated from 10 to 12 in the variables.tf file.

Running a terraform apply now will destroy the current random_string resource and then create a new one with the length that is 12 characters long.
```
We have to add this line to the string resource:
```
```
lifecycle {
        create_before_destroy =  true
    }
```
### Exercise 7/12
The resource block for the file resource has been updated! This will force the resource to be recreated during the next apply! But, before that, let's also add a lifecycle rule of create_before_destroy to this resource block.


When ready, apply the changes with terraform apply


Important: Once the lifecycle rule has been added, only run the apply command once. We will learn why soon.
```
We have to add this:
```
```
lifecycle {
      create_before_destroy = true
    }
```
### Exercise 8/12
Great! We have now added the lifecycle rule and forced the resources to be created first and then destroyed.

What is the id of the file resource we just created?

Run terraform show or terraform state show local_file.file to find out.
```bash
terraform state show local_file.file | grep id # this will return the 
```
### Exercise 9/12
Read the contents of the file /root/random_text manually. (Try opening with Visual Studio Code / cat command or a text editor)

What is the content of this file?
```bash
cat /root/random_text # No such file or directory
```
### Exercise 10/12
Where did the file go?!!?

If you observe the output of the previous apply (scroll up!), you will see that the lifecycle rule we applied caused the local file to the created first and the same file to be destroyed during the recreate operation.


This goes to show that it is not always advisable to use this rule!

In this example, the filename argument for the local_file resource has to be unique which means that we cannot have two instances of the same file created at the same time!
The random_string resource on the other hand is a logical resource that is only recorded in the state and does not have such a restriction.

If you run terraform apply again, the file resource will be created as it does not exist currently.
```
Then its so much important to check what you are doing...
```
### Exercise 11/12
We have now wiped out the resources that were created in this configuration directory and updated the main.tf file.


Now, it only contains a single random_pet resource called super_pet.

Under which circumstances will a new pet id be created?
```bash
If we change the variable's values, the `id` will also change.
Because it will create a new resource. 
```
### Exercise 12/12
Now, update the configuration so that the resource super_pet is not destroyed under any circumstances with a terraform destroy or terraform apply command.
```
https://developer.hashicorp.com/terraform/language/meta-arguments/lifecycle#prevent_destroy

if we look at the documentation, we can set `prevent_destroy = true` in lifecycle in order to block destroying this resource.
```

