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

Understanding linux services.

### Exercise 1/8
![alt text](image.png)
```bash
OK
```
### Exercise 2/8
![alt text](image-1.png)
```bash
dpkg
```
### Exercise 3/8
![alt text](image-2.png)
```bash
OK
```
### Exercise 4/8
![alt text](image-3.png)
```bash
# I couldn't install it:

# dpkg: error processing package firefox (--install):
#  dependency problems - leaving unconfigured
# Processing triggers for mime-support (3.60ubuntu1) ...
# Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
# Errors were encountered while processing:
#  firefox
```
### Exercise 5/8
![alt text](image-4.png)
```bash
Dependencies not met
```
### Exercise 6/8
![alt text](image-5.png)
```bash
sudo apt install /root/firefox.deb -y
```
### Exercise 7/8
![alt text](image-6.png)
```bash
sudo apt search Chromium
```
### Exercise 8/8
![alt text](image-7.png)
```bash
sudo apt remove chromium-browser
```