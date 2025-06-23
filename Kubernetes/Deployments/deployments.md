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

Understanding Kubernetes.

### Exercise 1/11
How many PODs exist on the system?

In the current(default) namespace.
```bash
kubectl get pods # none
```
### Exercise 2/11
How many ReplicaSets exist on the system?

In the current(default) namespace.
```bash
kubectl get rs # none
```
### Exercise 3/11
How many Deployments exist on the system?

In the current(default) namespace.
```bash
kubectl get deployments # none
```
### Exercise 4/11
How many Deployments exist on the system now?

We just created a Deployment! Check again!
```bash
kubectl get deployments # now its none
```
### Exercise 5/11
How many ReplicaSets exist on the system now?
```bash
kubectl get rs # now its "1"
```
### Exercise 6/11
How many PODs exist on the system now?
```bash
kubectl get pods # Now its "4"
```
### Exercise 7/11
Out of all the existing PODs, how many are ready?
```bash
kubectl get pods # None of them is ready!
```
### Exercise 8/11
What is the image used to create the pods in the new deployment?
```bash
kubectl describe pod | grep Image: # this returns: busybox888
```
### Exercise 9/11
Why do you think the deployment is not ready?
```
Images doesn't exist!
```
### Exercise 10/11
Create a new Deployment using the deployment-definition-1.yaml file located at /root/.

There is an issue with the file, so try to fix it.
```bash
# https://stackoverflow.com/questions/64686318/no-kind-deployment-is-registered-for-version-apps-v1-build-by-jenkinsfile
nano deployments-definition-1.yaml

# in the file, change this line:
# kind: deployment
# to
# kind: Deployment
```
### Exercise 11/11
Create a new Deployment with the below attributes using your own deployment definition file.

Name: httpd-frontend;  
Replicas: 3;  
Image: httpd:2.4-alpine  
```bash
# Create a .yaml file with the contents like this:

# apiVersion: apps/v1
# kind: Deployment
# metadata:
#   name: httpd-frontend
#   labels:
#     app: nginx
# spec:
#   replicas: 3
#   selector:
#     matchLabels:
#       app: httpd
#   template:
#     metadata:
#       labels:
#         app: httpd
#     spec:
#       containers:
#       - name: httpd
#         image: httpd:2.4-alpine
#         ports:
#         - containerPort: 80

# and then run:
kubectl apply -f sample.yaml
```
