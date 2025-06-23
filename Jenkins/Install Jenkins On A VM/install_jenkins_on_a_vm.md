## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/7](#exercise-17)
- [Exercise 2/7](#exercise-27)
- [Exercise 3/7](#exercise-37)
- [Exercise 4/7](#exercise-47)
- [Exercise 5/7](#exercise-57)
- [Exercise 6/7](#exercise-67)
- [Exercise 7/7](#exercise-77)

##  Introduction

Understanding Jenkins.

### Exercise 1/7
Which of the following options best describes what Jenkins is?
```
An Automation Server
```
### Exercise 2/7
What is CI/CD?

A. CI/CD refers to the continuous integration and continuous delivery/deployment process.

B. CI/CD refers to the automation of routine system administration tasks.

C. CI/CD is an application bug testing framework.

D. CI/CD is security management framework.
```
A
```
### Exercise 3/7
Can we use Jenkins to automate routine system administration tasks?
```
YES
```
### Exercise 4/7
Which of the following packages is a prerequisite for installing Jenkins ?
```
Java
```
### Exercise 5/7
Can we run Jenkins in a container ?
```bash
YESSS!!
```
### Exercise 6/7
Now let us install Jenkins on the centos-host machine and configure it to run on port 8090 instead of the default port 8080.


You can refer to the Jenkins Installation Docs located above the terminal.
```bash
# https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos

sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf upgrade
# Add required dependencies for the jenkins package
sudo dnf install fontconfig java-21-openjdk
sudo dnf install jenkins
sudo systemctl daemon-reload


# run these commands for installing jenkins.
# then run this command:
sudo vi /lib/systemd/system/jenkins.service 
# edit: Environment="JENKINS_PORT=8000" section

# lastly do this:
sudo systemctl start jenkins
```
### Exercise 7/7
Now, you should be able to access Jenkins using Jenkins button on the top bar. Complete its installation from UI and make sure to create first admin user as per details mentioned below:

Username: admin  
Password: Admin321  
Full name: Admin User  
E-mail address: admin@example.com  
```bash
DONE!
```