# How many PODs exist on the system?   
# How many ReplicaSets exist on the system?   
# How many Deployments exist on the system?

![Screenshot from 2023-10-24 10-25-40](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/cb61848d-8a43-42a3-ac3f-72c5f837af8a)


# How many Deployment exist on the system now?
# How many ReplicaSets exist on the system now?
# How many PODs exist on the system now?

![Screenshot from 2023-10-24 10-29-07](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/db2a1739-561a-4bef-950a-c1898438e666)

# Out of all the existing PODs, how many are ready? 
answer: 0 

![Screenshot from 2023-10-24 10-30-17](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/97fd0518-b4f7-4f4b-9447-4a3ae555493e)


# What is the image used to create the pods in the new deployment?

![Screenshot from 2023-10-24 10-34-24](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/41a28b17-b306-4540-bc8a-ecdf333de6ef)


# Why do you think the deployment is not ready?

```The image BUSYBOX888 doesn't exist```

# Create a new Deployment using the deployment-definition-1.yaml file located at /root/.


There is an issue with the file, so try to fix it.

CheckCompleteIncomplete
Name: deployment-1


![Screenshot from 2023-10-24 10-42-55](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/1141583d-b496-4fe9-82fc-b04c8426a82c)


The value for kind is incorrect. It should be Deployment with a capital D.

![Screenshot from 2023-10-24 10-43-45](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/28927f4a-c323-46b0-a28a-60ac2c9411dc)



# Create a new Deployment with the below attributes using your own deployment definition file.


Name: httpd-frontend;
Replicas: 3;
Image: httpd:2.4-alpine

CheckCompleteIncomplete
Name: httpd-frontend

Replicas: 3

Image: httpd:2.4-alpine


```ruby
controlplane ~ ➜  touch deployment-definition-httpd.yaml

controlplane ~ ➜  ls
deployment-definition-1.yaml      deployment-definition-httpd.yaml  sample.yaml

controlplane ~ ➜  vi deployment-definition-httpd.yaml 
```
![Screenshot from 2023-10-24 10-46-41](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/28394063-5a80-4f03-9df5-68fef5c95a2e)

``` kubectl create -f deployment-definition-httpd.yaml ```

![Screenshot from 2023-10-24 10-50-23](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/67f1dd3f-94f8-4663-9ae5-e7ed024c02e7)






