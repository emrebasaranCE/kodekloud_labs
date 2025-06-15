## Table of Contents

- [Introduction](#introduction)
- [Exercise 1/10](#exercise-110)
- [Exercise 2/10](#exercise-210)
- [Exercise 3/10](#exercise-310)
- [Exercise 4/10](#exercise-410)
- [Exercise 5/10](#exercise-510)
- [Exercise 6/10](#exercise-610)
- [Exercise 7/10](#exercise-710)
- [Exercise 8/10](#exercise-810)
- [Exercise 9/10](#exercise-910)
- [Exercise 10/10](#exercise-1010)

## Introduction

In this lab, our main aim is to understand using linux. Lets get started.

### Exercise 1/10

![alt text](image.png)

If we look at the given terminal, we can easily see that:
![alt text](image-1.png)

### Exercise 2/10

![alt text](image-2.png)

We can also see that there is no `test_file3.txt` in the `test_dir` directory. 

### Exercise 3/10

![alt text](image-3.png)

Lets create:

```bash
cd /home/thor
sudo nano empty_file.txt
# and save!
```

### Exercise 4/10

![alt text](image-4.png)

We can write this script without more work with echo:
```bash
cd /home/thor/
echo "This is not empty file" > contents_file.txt
```

### Exercise 5/10

![alt text](image-5.png)

```bash 
mkdir /home/thor/empty_dir
```

### Exercide 6/10

![alt text](image-6.png)

```bash
mkdir -p /home/thor/asia/india/bangalore
```

### Exercise 7/10

![alt text](image-7.png)

```bash
# Create some file
echo "Some info" > /home/thor/asia/bangalore.txt
cp -v /home/thor/asia/bangalore.txt /home/thor/asia/india/bangalore
# -v for better understanding about what is going on!
```

### Exercise 8/10

![alt text](image-8.png)

```bash
cp -vr /home/thor/asia/india/bangalore /home/thor
```

### Exercise 9/10

![alt text](image-9.png)

```bash
rm -v /home/thor/asia/bangalore.txt
```

### Exercise 10/10

![alt text](image-10.png)

```bash 
rm -vr /home/thor/asia/india/bangalore
```