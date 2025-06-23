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
How many Services exist on the system?
```bash
kubectl get services # 1
```
### Exercise 2/11
That is a default service created by Kubernetes at launch.
```
OK
```
### Exercise 3/11
What is the type of the default kubernetes service?
```bash
kubectl get services # the service shown to us is default service.
# which is "ClusterIP"
```
### Exercise 4/11
What is the targetPort configured on the kubernetes service?
```bash
kubectl describe service # this shows port 6443
```
### Exercise 5/11
How many labels are configured on the kubernetes service?
```bash
kubectl describe service # we got "2"
```
### Exercise 6/11
How many Endpoints are attached on the kubernetes service?
```bash
kubectl describe service # only "1"
```
### Exercise 7/11
How many Deployments exist on the system now?

In the current(default) namespace
```bash
kubectl get deployments # return "1" line
```
### Exercise 8/11
What is the image used to create the pods in the deployment?
```bash
kubectl describe deployment | grep Image:
# this returns the image name: "kodekloud/simple-webapp:red"
```
### Exercise 9/11
Are you able to accesss the Web App UI?

Try to access the Web Application UI using the tab simple-webapp-ui above the terminal.
```
No, i cannot.
```
### Exercise 10/11
Create a new service to access the web application using the service-definition-1.yaml file.

Name: webapp-service  
Type: NodePort  
targetPort: 8080  
port: 8080  
nodePort: 30080  
selector:  
  name: simple-webapp  
```bash
nano service-definition-1.yaml 

# and paste this:

# ---
# apiVersion: v1
# kind: Service
# metadata:
#   name: webapp-service
#   namespace: default
# spec:
#   ports:
#   - nodePort: 30080
    # port: 8080
    # targetPort: 8080
#   selector:
    # name: simple-webapp
#   type: NodePort


# then apply changes:
kubectl apply -f service-definition-1.yaml 
```
### Exercise 11/11
Access the web application using the tab simple-webapp-ui above the terminal window.
```
I can access it!
```
