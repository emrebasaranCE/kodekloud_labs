## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/5](#exercise-15)
- [Exercise 2/5](#exercise-25)
- [Exercise 3/5](#exercise-35)
- [Exercise 4/5](#exercise-45)
- [Exercise 5/5](#exercise-55)

##  Introduction

Understanding Ansible.

### Exercise 1/5
In this lab exercise you will use below hosts. Please note down some details about these hosts as given below :


student-node :- This host will act as an Ansible master node where you will create playbooks, inventory, roles etc and you will be running your playbooks from this host itself.


node01 :- This host will act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:


User: bob
Password: caleston123  


node02 :- This host will also act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:


User: bob
Password: caleston123  


Note: Please type exit or logout on the terminal or press CTRL + d to log out from a specific node.
```
OK
```
### Exercise 2/5
Can loops be executed on dictionary values in Ansible?
```
Yes
```
### Exercise 3/5
Which type of plugin with_* directives use in Ansible?
```
lookup
```
### Exercise 4/5
The playbook /home/bob/playbooks/fruits.yml currently runs an echo command to print a fruit name. Apply a loop directive (with_items) to the task to print all fruits defined under the fruits variable.
```yaml
# Our yaml file should look like this:
---
-  name: 'Print list of fruits'
   hosts: localhost
   vars:
     fruits:
       - Apple
       - Banana
       - Grapes
       - Orange
   tasks:
     - command: 'echo "{{ item }}"'
       with_items: '{{ fruits }}'
```
### Exercise 5/5
We are attempting to install multiple packages using the yum module for a more realistic use case. The playbook /home/bob/playbooks/packages.yml installs only a single package. Update it to install all packages defined under packages variable.
```yaml
# This is how our yaml file look like:
---
- name: 'Install required packages'
  hosts: localhost
  become: yes
  vars:
    packages:
      - httpd
      - make
      - vim
  tasks:
    - yum:
        name: '{{ item }}'
        state: present
      with_items: '{{ packages }}'
```