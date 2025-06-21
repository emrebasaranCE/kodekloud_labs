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
- [Exercise 9/8](#exercise-98)
- [Exercise 10/8](#exercise-108)
- [Exercise 11/8](#exercise-118)
- [Exercise 8/8](#exercise-8)


##  Introduction

Understanding linux services.

### Exercise 1/8
![alt text](image.png)
```
22
```
### Exercise 2/8
![alt text](image-1.png)
```
bob
```
### Exercise 3/8
![alt text](image-2.png)
```
OK
```
### Exercise 4/8
![alt text](image-3.png)
```bash
ssh-keygen
```
### Exercise 5/8
![alt text](image-4.png)
```
/home/bob/.ssh/id_rsa.pub.
```
### Exercise 6/8
![alt text](image-5.png)
```bash
# https://www.ssh.com/academy/ssh/copy-id

ssh-copy-id -i ~/.ssh/id_rsa bob@devapp01

# After copying the key, we can use this command for ssh connection:
ssh devapp01
```
### Exercise 7/8
![alt text](image-6.png)
```
/home/bob/.ssh/authorized_keys
```
### Exercise 8/8
![alt text](image-7.png)
```bash
# https://www.geeksforgeeks.org/scp-command-in-linux-with-examples/

scp /home/bob/caleston-code.tar.gz bob@devapp01:/home/bob/
```