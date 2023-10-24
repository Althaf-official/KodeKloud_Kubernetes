#  Deployment in Kubernetes

**Deployment** is a fundamental Kubernetes resource that is used to manage and control the deployment of applications or workloads in a Kubernetes cluster. It provides a higher-level abstraction for managing application updates and scaling.

Here are some key concepts to understand about Deployments:

1. **Desired State:** A Deployment allows you to declare the desired state of your application. You specify the number of desired replicas (instances) of your application that should be running at all times. Kubernetes will work to ensure that this desired state is maintained.

2. **Declarative Configuration:** Deployments are declared using YAML or JSON configuration files. You specify the details of your application, including the container image, resource requirements, labels, and more, in these configuration files.

3. **Rolling Updates:** One of the key features of Deployments is the ability to perform rolling updates. If you need to update your application to a new version, you can simply update the Deployment's configuration to use the new container image. Kubernetes will automatically manage the rollout, ensuring that a specified number of new pods are created while an equal number of old pods are terminated, maintaining the desired replica count.

4. **Scaling:** You can easily scale your application up or down by changing the replica count in the Deployment configuration. Kubernetes will take care of adding or removing pods to meet the new replica count.

5. **High Availability:** Deployments are designed to ensure high availability. If a pod fails for any reason, the Deployment controller will automatically replace it to maintain the desired number of replicas.

6. **Label-Based Selector:** Deployments use label-based selectors to manage pods. You specify labels in both your Deployment configuration and your pod template. The Deployment controller uses these labels to identify and manage the pods associated with the Deployment.

Here's an example of a simple Deployment configuration:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app-container
        image: my-app-image:latest
```

In this example, we define a Deployment named "my-deployment" with three replicas. The pod template specifies a container with the image "my-app-image:latest." The `app` label is used to match the pods controlled by this Deployment.

In summary, Deployments are a critical tool in Kubernetes for managing the lifecycle of applications, making it easier to deploy, update, and scale your workloads while ensuring high availability.










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


nmumshad's way:
![Screenshot from 2023-10-24 11-05-31](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/3fad9aed-5d25-4c09-ac05-ca68a79fec20)


my way:
```ruby
controlplane ~ ➜  touch deployment-definition-httpd.yaml

controlplane ~ ➜  ls
deployment-definition-1.yaml      deployment-definition-httpd.yaml  sample.yaml

controlplane ~ ➜  vi deployment-definition-httpd.yaml 
```
![Screenshot from 2023-10-24 10-46-41](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/28394063-5a80-4f03-9df5-68fef5c95a2e)

``` kubectl create -f deployment-definition-httpd.yaml ```

![Screenshot from 2023-10-24 10-50-23](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/67f1dd3f-94f8-4663-9ae5-e7ed024c02e7)






