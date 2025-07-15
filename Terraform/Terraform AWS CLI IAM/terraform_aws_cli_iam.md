## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/18](#exercise-118)
- [Exercise 2/18](#exercise-218)
- [Exercise 3/18](#exercise-318)
- [Exercise 4/18](#exercise-418)
- [Exercise 5/18](#exercise-518)
- [Exercise 6/18](#exercise-618)
- [Exercise 7/18](#exercise-718)
- [Exercise 8/18](#exercise-818)
- [Exercise 9/18](#exercise-918)
- [Exercise 10/18](#exercise-1018)
- [Exercise 11/18](#exercise-1118)
- [Exercise 12/18](#exercise-1218)
- [Exercise 13/18](#exercise-1318)
- [Exercise 14/18](#exercise-1418)
- [Exercise 15/18](#exercise-1518)
- [Exercise 16/18](#exercise-1618)
- [Exercise 17/18](#exercise-1718)
- [Exercise 18/18](#exercise-1818)


##  Introduction

Understanding Terraform.

### Exercise 1/18
From this lab onwards, we will be working with `aws` services! In this lab, we will learn how to make use of `aws cli` to explore and deploy `IAM resources` that we learnt in the previous lecture.
As explained in the Lab Demonstration video, we are making use of localstack as the mocking framework to work with `AWS`.

This framework is exposed at `http://aws:4566`. Hence, throughout this lab, we will be making use of the command option and parameter like this: `--endpoint http://aws:4566`
```bash
OK
```
### Exercise 2/18
What is the `aws cli` verison?
```bash
aws --version
```
### Exercise 3/18
Which `command` should be used to interact with `Identity and Access Management` in `AWS` using the `CLI`?

If unsure, use the CLI help by running: `aws <command> help`
```bash
aws help | grep iam # this retuns true
```
### Exercise 4/18
Which `subcommand` with `iam` can be used to list all the users created in `aws`?

If unsure, use the CLI help by running: `aws iam <subcommand>  help`
```bash
aws iam help | grep list-users # this value also returns true
```
### Exercise 5/18
Now, let's learn how to make use of the mocking framework used in the labs.

Run: `aws iam list-users`

Does it work?
```bash
NO
```
### Exercise 6/18
This is because, we have not provided the `--endpoint` option.
Now, run the same command but with the `--endpoint http://aws:4566` as the option, like this:
`aws --endpoint http://aws:4566 iam list-users`
```bash
aws --endpoint http://aws:4566 iam list-users

# Its works now!
```
### Exercise 7/18
How many IAM Users do you see listed now?
```
aws  --endpoint http://aws:4566 iam list-users
{
    "Users": [
        {
            "Path": "/",
            "UserName": "jill",
            "UserId": "vbnh2j5rfi4g1soueedn",
            "Arn": "arn:aws:iam::000000000000:user/jill",
            "CreateDate": "2025-07-14T07:42:06.953000+00:00"
        },
        {
            "Path": "/",
            "UserName": "jack",
            "UserId": "iiolky5rjdxgec0g018s",
            "Arn": "arn:aws:iam::000000000000:user/jack",
            "CreateDate": "2025-07-14T07:42:08.381000+00:00"
        }
    ]
}

```
```bash
2 user
```
### Exercise 8/18
Now let's add a few more users! To add more users, we need to make use of the `create-user` sub-command.
However, we also need to pass in a mandatory option with this command for it to work?

Which option should we use?
```bash
aws iam create-user help # in the output, we can see that its "--user-name"
```
### Exercise 9/18
Create a new user called mary using the AWS CLI.  

Make sure to use the --endpoint http://aws:4566 option with the command.
```bash
aws  --endpoint http://aws:4566 iam create-user --user-name mary
```
### Exercise 10/18
Now, inspect the newly created user `mary` and find out its `ARN (Amazon Resource Name)`.
```json
{
    "User": {
        "Path": "/",
        "UserName": "mary",
        "UserId": "wonv1fya49bnpyhgj74c",
        "Arn": "arn:aws:iam::000000000000:user/mary", # this line
        "CreateDate": "2025-07-14T07:50:10.789000+00:00"
    }
}
```
### Exercise 11/18
What is the default region that has been configured for use with the `AWS CLI`?
```bash
https://stackoverflow.com/questions/31331788/using-aws-cli-what-is-best-way-to-determine-the-current-region

aws configure get region
```
### Exercise 12/18
What is the `aws_access_key_id` used in the configuration?
```bash
aws configure get aws_access_key_id # this returns `foo`
```
### Exercise 13/18
What is the value of `aws_secret_access_key` used?
```bash
aws configure get aws_secret_access_key # this returns `bar`
```
### Exercise 14/18
Now that we have a few users created, let's grant them privileges.
Let's start with mary, grant her full administrator access by making use of the policy called AdministratorAccess.


Make use of the subcommand attach-user-policy.
The ARN of the AdministratorAccess policy is arn:aws:iam::aws:policy/AdministratorAccess.
```bash
# Turns out we have to figure out this is the command :')
aws --endpoint http://aws:4566 iam attach-user-policy --user-name mary --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
```
### Exercise 15/18
`jack` and `jill` are developers and are part of a project called `project-sapphire`.
Create a new `IAM Group` called `project-sapphire-developers`.


Use the subcommand `create-group` to create the group.
```bash
aws --endpoint http://aws:4566 iam create-group --group-name project-sapphire-developers
```
### Exercise 16/18
Add the IAM users called `jack` and `jill`, who are developers to the new IAM Group called `project-sapphire-developers`.

Use the subcommand `add-user-to-group` to add users into the group.
```bash
aws --endpoint http://aws:4566 iam add-user-to-group --group-name project-sapphire-developers --user-name jack
aws --endpoint http://aws:4566 iam add-user-to-group --group-name project-sapphire-developers --user-name jill
```
### Exercise 17/18
What privileges are granted for `jack` and `jill` who are part of the group `project-sapphire-developers`?

Check for their permissions individually and the ones granted to the group.
```bash
aws --endpoint http://aws:4566 iam list-attached-group-policies --group-name project-sapphire-developers

# we got none!
```
### Exercise 18/18
Both `jack` and `jill` need complete access to the EC2 service.


Attach the `AmazonEC2FullAccess` policy with the ARN: `arn:aws:iam::aws:policy/AmazonEC2FullAccess` to the group `project-sapphire-developers`.
```bash
aws --endpoint http://aws:4566 iam attach-group-policy --group-name project-sapphire-developers  --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess
```