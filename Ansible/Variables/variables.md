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

Understanding Ansible.

### Exercise 1/9
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
### Exercise 2/9
Can we define variables in an Ansible inventory file?
```bash
Yes
```
### Exercise 3/9
Can we define variables in an Ansible playbook?
```bash
Yes
```
### Exercise 4/9
Which of the following formats is used to call a variable in an Ansible playbook?
```bash
'{{variable name}}'
```
### Exercise 5/9
The /home/bob/playbooks/playbook.yaml playbook is adding a name server entry in /tmp/resolv.conf sample file on localhost. The name server information is already added to the /home/bob/playbooks/inventory file as a variable called nameserver_ip.

Replace the hardcoded ip address of the name server in this playbook to use the value from the variable defined in the inventory file. 

Note: You need not to execute this playbook as of now.
```bash
# we need to update hardcoded line like this:
line: 'nameserver {{  nameserver_ip  }}'
```
### Exercise 6/9
We have updated the /home/bob/playbooks/playbook.yaml playbook to add a new task to disable SNMP port on localhost. However, the port is hardcoded in the playbook. Update the playbook to replace the hardcoded value of the SNMP port to use the value from the variable named snmp_port, defined in the inventory file.

Note: You need not to execute this playbook as of now.
```bash
# we have to change this line:
port: '160-161'

# to:
port: '{{ snmp_port }}'
```
### Exercise 7/9
We have reset the /home/bob/playbooks/playbook.yaml playbook. Its printing some personal information of an employee. We would like to move the car_model, country_name and title values to the respective variables, and these variables should be defined at the play level.


Add three new variables named car_model, country_name and title under the play and move the values over there. Use these variables within the task to remove the hardcoded values.
```yaml
# this is the yaml file:
---
- hosts: localhost
  vars:
    car_model: 'BMW M3'
    country_name: USA
    title: 'Systems Engineer'
  tasks:
    - command: 'echo "My car is {{ car_model }}"'
    - command: 'echo "I live in the {{ country_name }}"'
    - command: 'echo "I work as a {{ title  }}"'
```
### Exercise 8/9
The /home/bob/playbooks/app_install.yaml playbook is responsible for installing a list of packages on a remote server(s). The list of packages to be installed is already added to the /home/bob/playbooks/inventory file as a list variable called app_list.

Right now the list of packages to be installed is hardcoded in the playbook. Update the /home/bob/playbooks/app_install.yaml playbook to replace the hardcoded list of packages to use the values from the app_list variable defined in the inventory file. Once updated, please run the playbook once to make sure it works fine.
```yaml
# edited file content: (i took it from solution, couldn't solve it.)
---
- hosts: all
  become: yes
  tasks:
    - name: Install applications
      yum:
        name: "{{ item }}"
        state: present
      with_items:
        - "{{ app_list }}"
```
### Exercise 9/9
The /home/bob/playbooks/user_setup.yaml playbook is responsible for setting up a new user on a remote server(s). The user details like username, password, and email are already added to the /home/bob/playbooks/inventory file as a dictionary variable called user_details.

Right now the user details is hardcoded in the playbook. Update the /home/bob/playbooks/user_setup.yaml playbook to replace the hardcoded values to use the values from the user_details variable defined in the inventory file. Once updated, please run the playbook once to make sure it works fine.
```yaml
---
- hosts: all
  become: yes
  tasks:
    - name: Set up user
      user:
        name: "{{ user_details.username }}"
        password: "{{ user_details.password }}"
        comment: "{{ user_details.email }}"
        state: present
```