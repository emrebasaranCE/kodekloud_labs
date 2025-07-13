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
A `data source` once created, can be used to `create`, `update`, and `destroy` infrastructure?

True or False?
```
FALSE
```
### Exercise 2/8
A data source can be created using `data` block. 

True or False?
```bash
TRUE
```
### Exercise 3/8
A new configuration directory has been created at `/root/terraform-projects/project-lexcorp`. A `data source` block is defined in the `main.tf` file to read the contents of an existing file.

There is also an `output` variable that uses reference expression to print the file content using this `data source`. However, there is something wrong!


Troubleshoot and fix the issue.


When ready, run `terraform init, plan and apply` to create the datasource. The configuration should print the output variable correctly.
```
# we have to create this file:

output "os-version" {
  value = data.local_file.os.content
}
data "local_file" "os" {
  filename = "/etc/os-release"
}
```
### Exercise 4/8
Now let's practice how to work with data sources from other providers.

The next few questions will be based on the aws provider.
Although we have only predominantly worked with local and the random provider, this exercise will help you learn how to work with different data sources using the documentation.

Don't worry if the configuration blocks and the arguments are unfamiliar. We will cover them in detail in the upcoming section.
```
OK 
```
### Exercise 5/8
We have now created a new configuration file called `ebs.tf` within the same configuration directory we have been working on.

What is the resource type that we are working with here?
```
data "aws_ebs_volume" "gp2_volume" {
  most_recent = true

  filter {
    name   = "volume-type"
    values = ["gp2"]
  }
}
```
```
Its `aws_ebs_volume`
```
### Exercise 6/8
Once this `data source` is created, how do we fetch the `Volume Id` for the resource that is created in `AWS`?

You may have to look up the documentation for this one. Documentation tab is available at the top right.
```
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ebs_volume

volume_id
```
### Exercise 7/8
Another file called `s3.tf` has now been created. It too has a `data source` that will be used to read data of an existing `s3` bucket.

However, there is a mistake in the argument used. What is wrong here?


You may have to look up the documentation for this one. Documentation tab is available at the top right.
```bash
`bucket_name` is not a valid argument!
```
### Exercise 8/8
We will get more practice with data sources and AWS resources in the upcoming lectures.
```bash
Great!
```