![Screenshot from 2023-10-26 11-22-52](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/dba35924-b2a9-4868-8ba3-136dabdc549a)


# Created 5 pods

![Screenshot from 2023-10-26 09-08-18](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/7344abdf-2e56-4a8c-a265-7939f9d90735)
The code snippet you've provided is a YAML configuration file used to create a Kubernetes Pod. Kubernetes is a container orchestration platform that manages the deployment, scaling, and management of containerized applications. In this case, you are defining a Pod that will run a PostgreSQL database container. Let's break down the YAML configuration:

1. `apiVersion: v1`: This field specifies the version of the Kubernetes API that this configuration file is using. In this case, it's using the "v1" version, which is the basic version of the API.

2. `kind: Pod`: This field specifies the type of Kubernetes resource being defined, which is a Pod. A Pod is the smallest deployable unit in Kubernetes and represents a single instance of a running process in a cluster.

3. `metadata`: This section contains metadata about the Pod, including its name and labels.

   - `name: postgres-pod`: This is the name of the Pod, which will be used to identify it within the cluster.

   - `labels`: Labels are key-value pairs that can be used to categorize and organize Pods. In this case, the Pod is labeled with two labels: "name: postgres-pod" and "app: demo-voting-app."

4. `spec`: The `spec` section describes the desired state of the Pod, including the container(s) it should run.

   - `containers`: This field specifies the list of containers to run in the Pod. In this case, there is one container defined:

     - `name: postgres`: This is the name of the container.

     - `image: postgres`: This specifies the Docker image to use for this container. In this case, it's using the official PostgreSQL image.

     - `ports`: This field specifies the ports that should be exposed by the container. The PostgreSQL database typically runs on port 5432, so it's being exposed here.

   - `env`: This field specifies environment variables to be set in the container:

     - `name: POSTGRES_USER` and `value: "postgres"`: These environment variables set the username and password for the PostgreSQL database. In this case, the username is "postgres," and the password is also "postgres."

This configuration file, when applied to a Kubernetes cluster, will create a Pod named "postgres-pod" running a PostgreSQL database container with the specified environment variables and port configuration. The labels can be used for organizing and selecting Pods within the cluster.

![Screenshot from 2023-10-26 09-08-32](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/c01b2cc6-6903-414a-8571-4792fec0dc4c)

The YAML configuration you provided describes a Kubernetes Pod named "voting-app-pod" running a specific containerized application. Let me break down the key parts:

- `apiVersion: v1` and `kind: Pod`: These lines indicate that you're defining a Pod, which is the smallest deployable unit in Kubernetes. A Pod can contain one or more containers that run together on the same network namespace.

- `metadata`: This section contains information about the Pod, such as its name and labels. Labels are key-value pairs that can be used to organize and categorize Pods. In this case, the Pod has two labels, "name" and "app."

- `spec`: This section specifies the desired state of the Pod.

  - `containers`: Here, you define the containers you want to run in the Pod. In this case, there's one container named "voting-app."

    - `name`: The name of the container, which is "voting-app."

    - `image`: Specifies the Docker image to use for the container. In this case, it's "kodekloud/examplevotingapp_vote:v1." This image likely contains the code and dependencies needed to run the "voting-app."

    - `ports`: You specify the ports that the container should listen on. In this case, it's listening on port 80, which is a common port for web applications.

So, in simple terms, this configuration defines a Pod called "voting-app-pod" that runs a single container named "voting-app." This container uses the "kodekloud/examplevotingapp_vote:v1" Docker image and listens on port 80. The labels are used for identifying and managing the Pod within the Kubernetes ecosystem, making it easier to manage and interact with this piece of your application.


![Screenshot from 2023-10-26 09-08-42](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/a3bb4b82-e7c5-4d0c-958a-e5d7a84dfdcd)
![Screenshot from 2023-10-26 09-08-55](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/4edf5683-7f3f-46e7-8b15-64213c91b840)
![Screenshot from 2023-10-26 09-09-05](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/4810c5d2-7c76-47b4-9c8b-d9b4eb04a3c5)


# Created-Internal service-definition file(ie: redis and postgres)

![Screenshot from 2023-10-26 09-30-59](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/c5968dbc-d087-43cf-b8e7-31c8e64eb273)
![Screenshot from 2023-10-26 09-31-21](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/5e88dbea-f594-492e-89e4-b0e2b037f535)
The code you provided appears to be a Kubernetes YAML configuration for a Service resource. In Kubernetes, a Service is used to expose a set of Pods as a network service, typically for enabling communication between different parts of an application. Let's break down the code snippet you provided:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: redis
  labels:
    name: redis-service
    app: demo-voting-app
```

1. `apiVersion: v1`: This line specifies the API version for this resource, which is typically set to "v1" for a Service in Kubernetes.

2. `kind: Service`: This line specifies that you are defining a Service resource.

3. `metadata`: This section provides metadata about the Service resource itself.

   - `name: redis`: This sets the name of the Service to "redis."

   - `labels`: This is a set of key-value labels associated with the Service. These labels can be used for various purposes, such as identifying or grouping resources.

4. `spec`: This section contains the specification for the Service, including how it should route network traffic to Pods.

   - `ports`: This is an array that defines the ports to be exposed by the Service. In this case, there is one port definition:

     - `port: 6379`: This specifies the port number on which the Service should listen (6379 in this case).

     - `targetPort: 6379`: This specifies the port on the Pods to which incoming traffic should be directed. This is typically the port that your application inside the Pods is listening on.

   - `selector`: This is used to select the Pods that the Service should route traffic to. The Service routes traffic to Pods that match the labels specified here. In this case, the selector specifies:

     - `name: redis-pod`: Select Pods with the label "name" set to "redis-pod."

     - `app: demo-voting-app`: Select Pods with the label "app" set to "demo-voting-app."

In summary, this YAML configuration defines a Kubernetes Service named "redis" with a label of "redis-service" and "demo-voting-app." It exposes port 6379 and routes traffic to Pods with the labels "name: redis-pod" and "app: demo-voting-app." This is typically used when you have a Redis database running in Pods, and you want to create a network service that allows other parts of your application to access Redis using the service name "redis" and port 6379.


# External Service(ie: voting and result)

![Screenshot from 2023-10-26 09-45-03](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/000abcec-ed25-43c1-a05c-20949b76088e)

![Screenshot from 2023-10-26 09-45-23](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/2eebf24f-08c4-4153-9889-9b8648c18d88)


The code you provided is another Kubernetes YAML configuration, defining a Service resource. Let's break it down step by step:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: voting-service
  labels:
    name: voting-service
    app: demo-voting-app
```

1. `apiVersion: v1`: This line specifies the API version for this resource, which is typically set to "v1" for a Service in Kubernetes.

2. `kind: Service`: This line specifies that you are defining a Service resource.

3. `metadata`: This section provides metadata about the Service resource itself.

   - `name: voting-service`: This sets the name of the Service to "voting-service."

   - `labels`: This is a set of key-value labels associated with the Service, just like in the previous example. In this case, the labels are "name: voting-service" and "app: demo-voting-app."

4. `spec`: This section contains the specification for the Service, including how it should expose network traffic.

   - `type: NodePort`: This specifies the type of the Service. A NodePort Service type exposes the Service on a port on each Node in the cluster, allowing external access to the Service.

   - `ports`: This is an array that defines the ports to be exposed by the Service. In this case, there is one port definition:

     - `port: 80`: This specifies the port number on which the Service should listen (port 80 in this case).

     - `targetPort: 80`: This specifies the port on the Pods to which incoming traffic should be directed. It's typically the port that your application inside the Pods is listening on (port 80 in this case).

     - `nodePort: 30005`: This specifies the port on the Nodes that will be opened for external access. In this case, external traffic to NodePort 30005 will be forwarded to the Service and then to the Pods.

   - `selector`: This is used to select the Pods that the Service should route traffic to. The Service routes traffic to Pods that match the labels specified here. In this case, the selector specifies:

     - `name: voting-app-pod`: Select Pods with the label "name" set to "voting-app-pod."

     - `app: demo-voting-app`: Select Pods with the label "app" set to "demo-voting-app."

In summary, this YAML configuration defines a Kubernetes Service named "voting-service" with labels "voting-service" and "demo-voting-app." It uses the NodePort type to expose port 80, directing incoming traffic to Pods with labels "name: voting-app-pod" and "app: demo-voting-app." The service is accessible externally via the Node's IP address on port 30005. This is commonly used to make applications accessible from outside the Kubernetes cluster, such as web applications.


### this is the difference between internal and external service 
```ruby
- `type: NodePort`: This specifies the type of the Service. A NodePort Service type exposes the Service on a port on each Node in the cluster, allowing external access to the Service.

   - `ports`: This is an array that defines the ports to be exposed by the Service. In this case, there is one port definition:

     - `port: 80`: This specifies the port number on which the Service should listen (port 80 in this case).

     - `targetPort: 80`: This specifies the port on the Pods to which incoming traffic should be directed. It's typically the port that your application inside the Pods is listening on (port 80 in this case).

     - `nodePort: 30005`: This specifies the port on the Nodes that will be opened for external access. In this case, external traffic to NodePort 30005 will be forwarded to the Service and then to the Pods.
```

# CREATE SERVICE


### check the folder
```ruby
althaf@mas:~/dev/kubernets/voting app$ ls
postgres-pod.yaml      redis.service.yaml       voting-app-pod.yaml
postgres-service.yaml  result-app-pod.yaml      voting-app-service.yaml
redis-pod.yaml         result-app-service.yaml  worker-app-pod.yaml
```
### created voting pod and service

```ruby
althaf@mas:~/dev/kubernets/voting app$ kubectl create -f voting-app-pod.yaml 
pod/voting-app-pod created


althaf@mas:~/dev/kubernets/voting app$ kubectl create -f voting-app-service.yaml 
service/voting-service created


althaf@mas:~/dev/kubernets/voting app$ kubectl get pod,svc
NAME                 READY   STATUS    RESTARTS   AGE
pod/voting-app-pod   1/1     Running   0          2m54s

NAME                     TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
service/kubernetes       ClusterIP   10.96.0.1      <none>        443/TCP        36d
service/voting-service   NodePort    10.107.4.105   <none>        80:30005/TCP   3s
```
### acces the service through minikube ip

```ruby
althaf@mas:~/dev/kubernets/voting app$ minikube service voting-service --url
http://192.168.49.2:30005
```
### and the url succesfully showed the voting app 

![Screenshot from 2023-10-26 10-17-19](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/25c0906b-5c07-47c3-b0dd-48c0d4feb9e5)



### created redis,postgres,result,voting pod and service
### created worker pod 
```ruby
kubectl create -f redis-service.yaml
kubectl create -f redis-pod.yaml 

```

now connected with the redis database . click is working now
![Screenshot from 2023-10-26 10-33-40](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/d0759c0c-4458-4848-a4aa-261c3e4af6e0)![Screenshot from 2023-10-26 10-33-47](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/553264b5-c8a2-4a37-8f7b-9302ea679147)

![Screenshot from 2023-10-26 11-12-35](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/9014f11c-f7c7-4b57-8146-fbcde0ea7ca0)


## succesfully intergrated with front 5 pod together

![Screenshot from 2023-10-26 11-17-11](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/963666fd-91ba-4a29-97cc-2e39637132ad)

![Screenshot from 2023-10-26 11-13-01](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/acc14f12-7470-409d-b034-f896489184da)
![Screenshot from 2023-10-26 11-13-12](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/14d8c7fb-ea84-48eb-a1d5-261aa5463cb6)















