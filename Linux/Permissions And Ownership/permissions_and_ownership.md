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

Understanding linux services.

### Exercise 1/9
![alt text](image.png)
```
OK
```
### Exercise 2/9
![alt text](image-1.png)
```bash
ls -la
```
### Exercise 3/9
![alt text](image-2.png)
```bash
ls -la 
# and we can see that "READ and EXECUTE"
```
### Exercise 4/9
![alt text](image-3.png)
```
NO PERMISSIONS
```
### Exercise 5/9
![alt text](image-4.png)
```
bob owns it
```
### Exercise 6/9
![alt text](image-5.png)
```bash
# https://www.pluralsight.com/resources/blog/tech-operations/linux-file-permissions

# If we follow this instructions:

chmod go-w soccer
```
### Exercise 7/9
![alt text](image-6.png)
```bash
chmod g+w soccer
chmod o-wrx soccer
```
### Exercise 8/9
![alt text](image-7.png)
```bash
# https://linuxize.com/post/linux-chown-command/

sudo chown mercury soccer 
```
### Exercise 9/9
![alt text](image-8.png)
```bash
sudo chown mercury -R sports/
```

