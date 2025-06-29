## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/19](#exercise-119)
- [Exercise 2/19](#exercise-219)
- [Exercise 3/19](#exercise-319)
- [Exercise 4/19](#exercise-419)
- [Exercise 5/19](#exercise-519)
- [Exercise 6/19](#exercise-619)
- [Exercise 7/19](#exercise-719)
- [Exercise 8/19](#exercise-819)
- [Exercise 9/19](#exercise-919)
- [Exercise 10/19](#exercise-1019)
- [Exercise 11/19](#exercise-1119)
- [Exercise 12/19](#exercise-1219)
- [Exercise 13/19](#exercise-1319)
- [Exercise 14/19](#exercise-1419)
- [Exercise 15/19](#exercise-1519)
- [Exercise 16/19](#exercise-1619)
- [Exercise 17/19](#exercise-1719)
- [Exercise 18/19](#exercise-1819)
- [Exercise 19/19](#exercise-1919)


##  Introduction

Understanding 

### Exercise 1/19
info
In this lab exercise you will use below hosts. Please note down some details about these hosts as given below:

student-node :- This host will act as an Ansible master node where you will create playbooks, inventory, roles etc and you will be running your playbooks from this host itself.

node01 :- This host will act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:

User: bob  
Password: caleston123  

node02 :- This host will also act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:

User: bob  
Password: caleston123  

Note: Please type exit or logout on the terminal or press CTRL + d to log out from a specific node.
```bash
OK
```
### Exercise 2/19
Which of the following Ansible modules support free_form parameter?
```bash
# Made some research but didnt find anything, the solution says its "Command"...
```
### Exercise 3/19
Does Ansible support idempotancy?
```bash
# https://infohub.delltechnologies.com/en-us/l/dell-powermax-ansible-modules-best-practices/idempotency-and-ansible-2/#:~:text=A%20key%20principle%20of%20Ansible,is%20the%20concept%20of%20idempotency.

Yes
```
### Exercise 4/19
Which of the following commands we can use to see the information about Ansible modules from command line?
```bash
ansible-doc
```
### Exercise 5/19
Which Ansible module is used in the following playbook?

```yaml
---
- hosts: localhost
  become: yes
  become_user: root
  tasks:
    - name: create user
      user:
        name: admin
```
```bash
user
```
### Exercise 6/19

Which of the following statements are true about lineinfile Ansible module?  

A. It only adds the given line in file if that line doesn't exist in that file.  
B. It adds the given line in file even if that line already exists in that file.  
C. It replaces all existing lines in the file with a new given line.  
D. It keeps the existing lines as well and add a new given line in the file.  
```bash
D & A
```
### Exercise 7/19
What are Ansible system modules used for?  

A. System modules are basically used to create/update files and directories.  
B. System modules are actions to be performed at a system level such as modifying the users and groups on a system, modifying iptables, starting/stopping the service etc.  
C. System modules are used to execute commands or scripts on a system.  
D. System modules are used to install and setup packages on a system.  
```bash
B
```
### Exercise 8/19

Your organization uses a proprietary cloud service that is not natively supported by Ansible. You need to develop a custom Ansible module to interact with this cloud service's API and provision resources.

Which type of the Ansible plugins allows you to integrate with a cloud provider's API for custom resource provisioning?  

a. Connection Plugin  
b. Lookup Plugin  
c. Module Plugin  
d. Action Plugin  
```bash
c
```
### Exercise 9/19
You've developed a custom module named custom_cloud. To test this module in a playbook named deploy.yml, which of the following task definitions is correct?


a.
```yaml
- name: Provision custom cloud resource
  action: custom_cloud
  args:
    param1: value1
    param2: value2
```
b.
```yaml
- name: Provision custom cloud resource
  module: custom_cloud
  parameters:
    - param1: value1
    - param2: value2
```
c.
```yaml
- name: Provision custom cloud resource
  custom_cloud:
    param1: value1
    param2: value2
```
d.
```yaml
- name: Provision custom cloud resource
  use_module: custom_cloud
  with_args:
    param1: value1
    param2: value2
```
```bash
c
```
### Exercise 10/19
You are tasked with setting up an Ansible playbook that automates the deployment of applications on AWS ec2 instances. Before running the playbook, you need to ensure that Ansible has an up-to-date inventory of all ec2 instances in your AWS account.

Which type of Ansible plugin would you use to fetch real-time information about your AWS ec2 instances?

a. Lookup Plugin  
b. Filter Plugin  
c. Callback Plugin  
d. Dynamic Inventory Plugin  

```bash
d
```
### Exercise 11/19

You have a custom dynamic inventory script named aws_inventory.py. Which command would you use to list all hosts in your AWS inventory using this script?

a. ansible-inventory --list -i aws_inventory.py  
b. ansible-playbook --inventory aws_inventory.py  
c. ansible aws_inventory.py --list-hosts  
d. ansible-list --inventory aws_inventory.py  
```bash
a
```
### Exercise 12/19
You are tasked with finding a collection in Ansible that provides modules specifically designed for managing Cisco IOS devices. Using the Modules & Plugins Index, which of the following collections is best suited for this purpose?


a. cisco.config  
b. cisco.ios  
c. cisco.setup  
d. cisco.network  
```bash
b
```
### Exercise 13/19
Which of the following is not a common connection parameter used by modules within the cisco.ios collection for managing Cisco IOS devices?

a. hostname  
b. password  
c. ios_version  
d. username  
```bash
c
```
### Exercise 14/19
Next

14 / 19
Which of the following Ansible versions is cisco.ios module likely to be compatible with?

Note: This can be a hypothetical answer; the actual version compatibility would need to be checked in the Modules & Plugins Index.

a. Ansible 1.5  
b. Ansible 2.8  
c. Ansible 3.1  
d. Ansible 4.0  
```bash
b
```
### Exercise 15/19
You're planning to deploy an application on AWS and need to set up ec2 instances using Ansible. Which module is primarily used for managing ec2 instances?


a. aws_instance  
b. aws_ec2_config  
c. ec2_instance  
d. aws_setup
```bash
# https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_instance_module.html

c
```
### Exercise 16/19

Update the playbook named playbook.yaml under /home/bob/playbooks directory with a task named Execute a script to run a script. The script is located at /tmp/install_script.sh on student-node.

Use the script module.  

Note: There is already an inventory file /home/bob/playbooks/inventory present on student-node system.
```bash
# https://docs.ansible.com/ansible/latest/collections/ansible/builtin/script_module.html

# we add these lines:

tasks:
   - name: 'Execute a script'
     script: '/tmp/install_script.sh'

# then run this code:
ansible-playbook -i inventory playbook.yaml
```
### Exercise 17/19
Update the playbook /home/bob/playbooks/playbook.yaml to add a new task to start httpd service on all web nodes defined in /home/bob/playbooks/inventory file. 

Use the service module.  

```yaml
# add this lines.
- name: 'Run httpd service'
  service: 
    name: httpd 
    state: started
```
```bash
# and then run this code:
ansible-playbook -i inventory playbook.yaml
```

### Exercise 18/19
Update the playbook /home/bob/playbooks/playbook.yaml to append the /var/www/html/index.html file on all web nodes. The line needs to be added is Welcome to ansible-beginning course, create the index.html file if doesn't exist.

Use the lineinfile module.
```bash
# https://dev.to/spacelift/ansible-modules-how-to-use-them-efficiently-examples-5gl6

- name: "Create or update index.html file."
  lineinfile:
    path: /var/www/html/index.html
    line: "Welcome to ansible-beginning course"
    create: true

# after adding this lines to the yaml file, we can run this command now;
ansible-playbook -i inventory playbook.yaml
```
### Exercise 19/19
Update the playbook /home/bob/playbooks/playbook.yaml to add a new task to create a new user called web_user.

Use the user module for this task. You can find the user details as below.

Username: web_user  
uid: 1040  
group: developers  
```bash
- name: 'Create a new user'
  user:
    name: 'web_user'
    uid: 1040
    group: 'developers'

# after adding this lines to the yaml file, we can now run the command for ansible:
ansible-playbook -i inventory playbook.yaml
```