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

Understanding Ansible.

### Exercise 1/11
In this lab exercise you will use below hosts. Please note down some details about these hosts as given below :

student-node :- This host will act as an Ansible master node where you will create playbooks, inventory, roles etc and you will be running your playbooks from this host itself.

node01 :- This host will act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:   
User: bob  
Password: caleston113  

node02 :- This host will also act as an Ansible client/remote host where you will setup/install some stuff using Ansible playbooks. Below are the SSH credentials for this host:  
User: bob  
Password: caleston113  

Note: Please type exit or logout on the terminal or press CTRL + d to log out from a specific node.  
```
OK
```
### Exercise 2/11
Look into the given sample inventory, which of the following formats this inventory is using?
```
web ansible_host=webserver.com
db ansible_host=dbserver.com
```
```
Ini
```
### Exercise 3/11
Which of the following ports Ansible uses by default to connect to the Linux remote hosts?
```
ssh
22  
```
### Exercise 4/11
Which of the following inventory parameters can be used to establish a local connection instead of ssh in Ansible?
```
ansible_connection
```
### Exercise 5/11
What value we must set for ansible_connection parameter to connect to a Windows server?
```bash
# https://docs.ansible.com/ansible/latest/os_guide/intro_windows.html
winRM
```
### Exercise 6/11
We have a sample inventory file called inventory under /home/bob/playbooks directory. It has 3 servers listed, add another server called server4.company.com in this file.
```INI                                            
# Sample Inventory File
server1.company.com
server2.company.com
server3.company.com
```

Edited file content:
```
# Sample Inventory File

server1.company.com
server2.company.com
server3.company.com
server4.company.com
```
### Exercise 7/11
We have reset the /home/bob/playbooks/inventory inventory file, and added the aliases named web1, web2 and web3 for the first three hosts respectively. Update this inventory file to add an alias called db1 for server4.company.com host.
```INI
# Sample Inventory File

web1 ansible_host=server1.company.com
web2 ansible_host=server2.company.com
web3 ansible_host=server3.company.com
```
```INI
; https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html

; Lines added:
db1 ansible_host=server4.company.com
```
### Exercise 8/11
As per the details given in the table below, you can see that, the web servers are linux based hosts and the db server is a Windows machine.  

Update the inventory /home/bob/playbooks/inventory to add a similar entry for server4.company.com host. Find the required details from the table below.  

As per the details given in the table below, you can see that, the web servers are linux based hosts and the db server is a Windows machine.


Update the inventory /home/bob/playbooks/inventory to add a similar entry for server4.company.com host. Find the required details from the table below.


| Alias | Host                   | Connection | User          | Password       |
|-------|------------------------|------------|---------------|----------------|
| web1  | server1.company.com    | ssh        | root          | Password123!   |
| web2  | server2.company.com    | ssh        | root          | Password123!   |
| web3  | server3.company.com    | ssh        | root          | Password123!   |
| db1   | server4.company.com    | winrm      | administrator | Dbp@ss123!     |

Note: For Linux based hosts, use ansible_ssh_pass parameter and for Windows based hosts, use ansible_password parameter.
Note: For Linux based hosts, use ansible_ssh_pass parameter and for Windows based hosts, use ansible_password parameter.
```INI                                             
# Sample Inventory File

# Web Servers
web1 ansible_host=server1.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web2 ansible_host=server2.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web3 ansible_host=server3.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
```
```INI
# Line added:
db1 ansible_host=server4.company.com ansible_connection=winrm ansible_user=administrator ansible_password=Dbp@ss123!
```
### Exercise 9/11
We have updated the /home/bob/playbooks/inventory file and added a group called web_servers for web servers. Similarly, add a group called db_servers for database servers.
```INI
# Sample Inventory File

# Web Servers
web1 ansible_host=server1.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web2 ansible_host=server2.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web3 ansible_host=server3.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!

# Database Servers
db1 ansible_host=server4.company.com ansible_connection=winrm ansible_user=administrator ansible_password=Passw>


[web_servers]
web1
web2
web3
```

```INI
# Lines added:
[db_servers]
db1
```
### Exercise 10/11
Let us now create a group of groups. Create a new group called all_servers and add the previously created groups web_servers and db_servers under it.  

Note: Syntax would be as follows -

```INI
[parent_group:children]
child_group1
child_group2
```
---

```INI
# Sample Inventory File

# Web Servers
web1 ansible_host=server1.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web2 ansible_host=server2.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!
web3 ansible_host=server3.company.com ansible_connection=ssh ansible_user=root ansible_ssh_pass=Password123!

# Database Servers
db1 ansible_host=server4.company.com ansible_connection=winrm ansible_user=administrator ansible_password=Password123!


[web_servers]
web1
web2
web3

[db_servers]
db1
```
```INI
# Lined added:
[all_servers:children]
web_servers
db_servers
```
### Exercise 11/11
Update the /home/bob/playbooks/inventory file to represent the data given in the below table in Ansible Inventory format.

| Server Alias | Server Name    | OS    | User          | Password  |
|--------------|----------------|-------|---------------|-----------|
| sql_db1      | sql01.xyz.com  | Linux | root          | Lin$Pass  |
| sql_db2      | sql02.xyz.com  | Linux | root          | Lin$Pass  |
| web_node1    | web01.xyz.com  | Win   | administrator | Win$Pass  |
| web_node2    | web02.xyz.com  | Win   | administrator | Win$Pass  |
| web_node3    | web03.xyz.com  | Win   | administrator | Win$Pass  |

Group the servers together based on this table

| Group         | Members                          |
|---------------|----------------------------------|
| db_nodes      | sql_db1, sql_db2                 |
| web_nodes     | web_node1, web_node2, web_node3  |
| boston_nodes  | sql_db1, web_node1               |
| dallas_nodes  | sql_db2, web_node2, web_node3    |
| us_nodes      | boston_nodes, dallas_nodes       |

```INI
# Lines added:

[db_nodes]
sql_db1
sql_db2

[web_nodes]
web_node1
web_node2
web_node3

[boston_nodes]
sql_db1
web_node1

[dallas_nodes]
sql_db2
web_node2
web_node3

[us_nodes:children]
boston_nodes
dallas_nodes
```