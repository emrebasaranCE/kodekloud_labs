## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/20](#exercise-120)
- [Exercise 2/20](#exercise-220)
- [Exercise 3/20](#exercise-320)
- [Exercise 4/20](#exercise-420)
- [Exercise 5/20](#exercise-520)
- [Exercise 6/20](#exercise-620)
- [Exercise 7/20](#exercise-720)
- [Exercise 8/20](#exercise-820)
- [Exercise 9/20](#exercise-920)
- [Exercise 10/20](#exercise-1020)
- [Exercise 11/20](#exercise-1120)
- [Exercise 12/20](#exercise-1220)
- [Exercise 13/20](#exercise-1320)
- [Exercise 14/20](#exercise-1420)
- [Exercise 15/20](#exercise-1520)
- [Exercise 16/20](#exercise-1620)
- [Exercise 17/20](#exercise-1720)
- [Exercise 18/20](#exercise-1820)
- [Exercise 19/20](#exercise-1920)
- [Exercise 20/20](#exercise-2020)


##  Introduction

Understanding Ansible.

### Exercise 1/20
In this lab exercise you will use below hosts. Please note down some details about these hosts as given below :  

student-node :- This host will act as an Ansible master node where you will create playbooks, inventory, roles etc and you will be running your playbooks from this host itself.  

node01 :- This host will act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:  

User: bob  
Password: caleston123  

node02 :- This host will also act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:  

User: bob  
Password: caleston203  

Note: Please type exit or logout on the terminal or press CTRL + d to log out from a specific node.  
```
OK
```
### Exercise 2/20
Which of the following formats is the Ansible playbook written in?
```
yaml
```
### Exercise 3/20
How many Ansible plays are there in the following given playbook?
```yaml
---
- name: Setup apache
  hosts: webserver
  tasks:
    - name: install httpd
      yum:
        name: httpd
        state: installed
    - name: Start service
      service:
        name: httpd
        state: started

- name: Setup tomcat
  hosts: appserver
  tasks:
    - name: install httpd
      yum:
        name: tomcat
        state: installed
    - name: Start service
      service:
        name: tomcat
        state: started
```
```
2
```
### Exercise 4/20
How many tasks are there under Setup apache Ansible play?
```yaml
---
- name: Setup apache
  hosts: webserver
  tasks:
    - name: install httpd
      yum:
        name: httpd
        state: installed
    - name: Start service
      service:
        name: httpd
        state: started

- name: Setup tomcat
  hosts: appserver
  tasks:
    - name: install httpd
      yum:
        name: tomcat
        state: installed
    - name: Start service
      service:
        name: tomcat
        state: started
```
```
2
```
### Exercise 5/20
If we use the following inventory, on which hosts will Ansible install the httpd package using the given playbook?


```INI
[webserver]
web1
web2
[appserver]
app1
app2
app3
```

```yaml
---
- name: Setup apache
  hosts: webserver
  tasks:
    - name: install httpd
      yum:
        name: httpd
        state: installed

- name: Setup tomcat
  hosts: appserver
  tasks:
    - name: install httpd
      yum:
        name: tomcat
        state: installed 
```

```
web1 and web2
```
### Exercise 6/20
Which of the following commands can you use to run an Ansible playbook named install.yaml?  

(A) ansible-playbook install.yaml  
(B) ansible-playbook run install.yaml  
(C) ansible-playbook -p install.yaml  
(D) ansible-playbook -i install.yaml
```
A
```
### Exercise 7/20
A sample playbook named update_service.yml is shown below, it is supposed to update a service on your servers.

```yaml
- hosts: all
  tasks:
    - name: Install a new package
      apt:
        name: new_package
        state: present

    - name: Update the service
      service:
        name: my_service
        state: restarted

    - name: Check service status
      service:
        name: my_service
        state: started
```
Which command would you use to run update_service.yml playbook in check mode?


A. ansible update_service.yml  
B. ansible-playbook update_service.yml --check  
C. ansible-playbook update_service.yml  
D. ansible-playbook --check update_service.yml  
```
B
```
### Exercise 8/20
Consider again the same sample playbook named update_service.yml as shown below.

```yaml
- hosts: all
  tasks:
    - name: Install a new package
      apt:
        name: new_package
        state: present

    - name: Update the service
      service:
        name: my_service
        state: restarted

    - name: Check service status
      service:
        name: my_service
        state: started
```

Let's suppose you have already ran this playbook on your server. Now, once you run this playbook in check mode against same server, which tasks would result in changed status?  

A. Install a new package  
B. Update the service  
C. Check service status  
D. All of the tasks  

```
B
```
### Exercise 9/20
There is another sample playbook named configure_database.yml that modifies a configuration file on your database servers. The initial code sample is as follows:
```yaml
- hosts: all
  tasks:
    - name: Set max connections
      lineinfile:
        path: /etc/postgresql/12/main/postgresql.conf
        line: 'max_connections = 500'

    - name: Set listen addresses
      lineinfile:
        path: /etc/postgresql/12/main/postgresql.conf
        line: 'listen_addresses = "*"'
``` 
Which command would you use to run the configure_database.yml playbook in both check mode and diff mode?  

A. ansible-playbook configure_database.yml --diff  
B. ansible-playbook configure_database.yml --check  
C. ansible-playbook configure_database.yml --check --diff  
D. ansible-playbook --diff --check configure_database.yml  
```bash
C
```
### Exercise 10/20
Consider again the same sample playbook named configure_database.yml as shown below.

```yaml
- hosts: all
  tasks:
    - name: Set max connections
      lineinfile:
        path: /etc/postgresql/12/main/postgresql.conf
        line: 'max_connections = 500'

    - name: Set listen addresses
      lineinfile:
        path: /etc/postgresql/12/main/postgresql.conf
        line: 'listen_addresses = "*"'
```



To check the configure_database.yml playbook for syntax errors, which command would you use?


A. ansible-playbook configure_database.yml   
B. ansible-playbook configure_database.yml --syntax  
C. ansible-playbook --syntax-check configure_database.yml  
D. ansible configure_database.yml --syntax-check  
```bash
C
```
### Exercise 11/20
You've been given a playbook named database_setup.yml that is supposed to set up a PostgreSQL database on your servers. Before deploying it, you want to ensure that it adheres to best practices and doesn't have any style-related issues.

The initial sample playbook is as follows:
```yaml
- name: Database Setup Playbook
  hosts: db_servers
  tasks:
    - name: Ensure PostgreSQL is installed
      apt:
        name: postgresql
        state: latest
        update_cache: yes

    - name: Start PostgreSQL service
      service:
        name: postgresql
        state: started

    - copy:
        src: /path/to/pg_hba.conf
        dest: /etc/postgresql/12/main/pg_hba.conf
      notify:
        - Restart PostgreSQL
``` 
Which command would you use to run ansible-lint on the database_setup.yml playbook?


A. ansible database_setup.yml --lint  
B. ansible-lint database_setup.yml  
C. ansible-playbook database_setup.yml --lint  
D. lint-ansible database_setup.yml  
```bash
B
```
### Exercise 12/20
Consider again the same sample playbook named database_setup.yml as shown below.

```yaml
- name: Database Setup Playbook
  hosts: db_servers
  tasks:
    - name: Ensure PostgreSQL is installed
      apt:
        name: postgresql
        state: latest
        update_cache: yes

    - name: Start PostgreSQL service
      service:
        name: postgresql
        state: started

    - copy:
        src: /path/to/pg_hba.conf
        dest: /etc/postgresql/12/main/pg_hba.conf
      notify:
        - Restart PostgreSQL
```
After running ansible-lint on the playbook, which of the following issues might you expect to see?


A. Incorrect indentation.  
B. Deprecated 'apt' module.  
C. Missing 'name' attribute for a task.  
D. Use of a blacklisted command.  
```bash
A & C
```
### Exercise 13/20
You've been given feedback from ansible-lint about potential issues in your hypothetical webserver_setup.yml playbook. The feedback mentions issues with indentation, deprecated modules, and missing name attributes.

Which of the following is NOT a recommended action based on the feedback?

A. Correcting the indentation in the playbook.  
B. Replacing deprecated modules with their newer counterparts.  
C. Ignoring the feedback and proceeding with playbook execution.  
D. Adding 'name' attributes to tasks that are missing them.   
```bash
C
```
### Exercise 14/20

If ansible-lint provides no output after checking a playbook, what does it indicate?

A. The playbook has syntax errors.  
B. The playbook is empty.  
C. The playbook adheres to best practices and has no style-related issues.  
D. ansible-lint failed to check the playbook.  
```bash
C
```
### Exercise 15/20
Update the name of the play in /home/bob/playbooks/playbook.yaml playbook to Execute a date command on localhost.  
```bash
# after editing yaml file, we have to run like this:
ansible-playbook -i inventory playbook.yaml
```
### Exercise 16/20
Update the playbook /home/bob/playbooks/playbook.yaml to add a task name Task to display hosts file for the existing task.
```bash
# after adding this line:
 - name: 'Task to display hosts file'

# run this command:
ansible-playbook -i inventory playbook.yaml
```
### Exercise 17/20
We have reset the playbook /home/bob/playbooks/playbook.yaml, now update it to add another task. The new task must execute the command cat /etc/resolv.conf and set its name to Task to display nameservers.
```bash    
# after adding this lines to tasks;
- name: 'Task to display nameservers'
  command: 'cat /etc/resolv.conf'

# run this command:
ansible-playbook -i inventory playbook.yaml
```
### Exercise 18/20
So far, we have been running all tasks on localhost. We would now like to run these tasks on node01, this host is already defined in /home/bob/playbooks/inventory file. Update the playbook /home/bob/playbooks/playbook.yaml to run the tasks on the node01 host.
```bash
# All we need to change 'localhost' to 'node01' and then:
ansible-playbook -i inventory playbook.yaml
```
### Exercise 19/20
Refer to the /home/bob/playbooks/inventory file. We would like to run the /home/bob/playbooks/playbook.yaml on all servers defined under web_nodes group.  

Note: Use the group name in playbook as defined in the inventory file.
```bash

```
### Exercise 20/20
Update the /home/bob/playbooks/playbook.yaml to add a new play named Execute a command on node02, and a task under it to execute cat /etc/hosts command on node02 host, name the task Task to display hosts file on node02.

Refer to the given inventory file.
```
We have to add this lines to playbook.yaml
```
```yaml
- name: 'Execute a command on node02'
  hosts: node02
  tasks:
    - name: 'Task to display hosts file on node02'
      command: 'cat /etc/hosts'
```
```bash
# Then to run this:
ansible-playbook -i inventory playbook.yaml
```