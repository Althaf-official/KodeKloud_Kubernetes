![image](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/224c234e-63d4-4cc0-9a79-b6ea8f2391c4)# Create a new pod with the nginx image.

Use the kubectl run command with the correct image.

```ruby
controlplane ~ ➜  kubectl run nginx --image=nginx
pod/nginx created

controlplane ~ ➜  kubectl get pods
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          13s
```
The command `kubectl run nginx --image=nginx` is used in the context of Kubernetes, a popular container orchestration platform, to create and deploy a containerized application.

Here's a breakdown of the command:

1. `kubectl`: This is the command-line tool for interacting with a Kubernetes cluster. It allows you to manage and control various aspects of your Kubernetes environment.

2. `run`: This is a subcommand of `kubectl` that is used to create and manage resources in a Kubernetes cluster. In this case, it's used to create a new deployment or pod.

3. `nginx`: This is the name given to the resource you're creating. In this context, it represents the name of the deployment or pod that will be created. You can choose any name you like for your resource.

4. `--image=nginx`: This is a flag that specifies the container image to use for the deployment or pod named "nginx." In this example, it's using the official NGINX container image, which is publicly available on Docker Hub. This flag tells Kubernetes to create a deployment or pod running the NGINX web server.

So, when you run the command `kubectl run nginx --image=nginx`, Kubernetes will create a deployment or pod named "nginx" and run the NGINX container within it. This will make the NGINX web server accessible within your Kubernetes cluster. You can then further configure and manage this deployment using other Kubernetes commands and resources.


# What is the image used to create the new pods?


You must look at one of the new pods in detail to figure this out.

Use the kubectl describe command.

```ruby

Containers:
  busybox:
    Container ID:  containerd://4d3ad8dcb65072e6d6113e7411f58f9085483840f8a719157f593e7719e52072
    Image:         busybox        <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
    Image ID:      docker.io/library/busybox@sha256:3fbc632167424a6d997e74f52b878d7cc478225cffac6bc977eedfe51c7f4e79
    Port:          <none>
    Host Port:     <none>
    Command:
      sleep
      1000
    State:          Running
      Started:      Mon, 23 Oct 2023 09:08:25 +0000
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-mxg4g (ro)
Conditions:
  Type              Status
  Initialized       True 
  Ready             True 
  ContainersReady   True 
  PodScheduled      True 
Volumes:
  kube-api-access-mxg4g:
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  119s  default-scheduler  Successfully assigned default/newpods-x5xhf to controlplane
  Normal  Pulling    118s  kubelet            Pulling image "busybox"
  Normal  Pulled     118s  kubelet            Successfully pulled image "busybox" in 341.828969ms (341.857388ms including waiting)
  Normal  Created    117s  kubelet            Created container busybox
  Normal  Started    117s  kubelet            Started container busybox
```
![Screenshot from 2023-10-23 13-13-53](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/3f70156c-c016-4056-9966-ab7b33504e18)

# Which nodes are these pods placed on?


You must look at all the pods in detail to figure this out.

Run the command `kubectl describe pod newpods-<id>` and look at the `node` field.
Alternatively run `kubectl get pods -o wide` and check for the node the pod is placed on.

![Screenshot from 2023-10-23 13-17-46](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/f8b9fb49-2c9b-4b8a-b6fb-3be0c299dd85)

# How many containers are part of the pod webapp?

### Run the command `kubectl describe pod webapp` and look under the Containers section

![Screenshot from 2023-10-23 13-24-31](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/c7ab6fdd-fa5f-444d-b252-4aad9e120a32)

# What images are used in the new webapp pod?


You must look at all the pods in detail to figure this out.

![Screenshot from 2023-10-23 13-33-03](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/f10ec81a-6cd5-4b82-9aae-97411ccac8bb)
nginx&agentx

# What is the state of the container agentx in the pod webapp?


Wait for it to finish the ContainerCreating state

aws:waiting

![Screenshot from 2023-10-23 13-34-38](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/bef2b761-a05a-4192-a2fe-6c079e6748c5)


# Why do you think the container agentx in pod webapp is in error?

A Docker image with this name doesn't exist on Docker Hub

```ruby
agentx:
    Container ID:   
    Image:          agentx
    Image ID:       
    Port:           <none>
    Host Port:      <none>
    State:          Waiting
      Reason:       ImagePullBackOff   <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
    Ready:          False
    Restart Count:  0
    Environment:    <none>
    Mounts:
```
# What does the READY column in the output of the kubectl get pods command indicate?

answer : running container in pods /Total container in pods


![Screenshot from 2023-10-23 13-45-54](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/b2b8d6ca-2629-4a14-a5a9-b27633d35f85)


# Delete the webapp Pod.


Once deleted, wait for the pod to fully terminate.


![Screenshot from 2023-10-23 15-17-28](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/2e558118-814f-459e-be2f-e0241193a7c4)


# Create a new pod with the name redis and the image redis123.


Use a pod-definition YAML file. And yes the image name is wrong!


Name: redis

Image name: redis123

We use kubectl run command with `--dry-run=client -o yaml` option to create a manifest file :-
### `kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml`
The command `kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml` is used to generate a Kubernetes resource definition in YAML format for a Redis deployment without actually creating the deployment in the cluster. Here's a breakdown of the command:

1. `kubectl`: This is the command-line tool for interacting with a Kubernetes cluster.

2. `run`: This is a subcommand of `kubectl` that is used to create and manage resources in a Kubernetes cluster, including deploying applications.

3. `redis`: This is the name you're giving to the resource you're creating. In this context, it represents the name of the deployment that will be generated.

4. `--image=redis123`: This flag specifies the container image to use for the deployment. It tells Kubernetes to use the "redis123" container image when creating the resource. However, please note that "redis123" is not an official Redis image, and you should replace it with a valid Redis image name if you intend to use a real Redis image.

5. `--dry-run=client`: This flag is used to simulate creating the resource without actually applying it to the cluster. In this "client" mode, the command checks for errors in the resource specification without making any changes to the cluster.

6. `-o yaml`: This flag specifies the output format for the generated resource. In this case, it's set to YAML, which means the result will be a YAML-formatted resource definition.

7. `> redis-definition.yaml`: This part of the command redirects the output to a file named "redis-definition.yaml." The YAML representation of the resource will be saved to this file.

So, when you run the command, it will generate a Kubernetes resource definition for a Redis deployment using the specified container image ("redis123"), but it won't actually create the deployment in the cluster. Instead, it will save the resource definition in a YAML file named "redis-definition.yaml" for further inspection or potential modification before applying it to the Kubernetes cluster at a later time.


After that, using `kubectl create -f` command to create a resource from the manifest file :-

### `kubectl create -f redis-definition.yaml`
The command `kubectl create -f redis-definition.yaml` is used to create or apply Kubernetes resources defined in a YAML file (in this case, "redis-definition.yaml") to a Kubernetes cluster. Here's a breakdown of the command:

1. `kubectl`: This is the command-line tool for interacting with a Kubernetes cluster.

2. `create`: This is a subcommand of `kubectl` that is used to create or apply resources in a Kubernetes cluster. It can be used to create or update various types of resources, such as deployments, pods, services, and more.

3. `-f redis-definition.yaml`: This part of the command specifies the file containing the resource definitions you want to apply to the cluster. In this case, "redis-definition.yaml" is the YAML file that contains the configuration for a Redis deployment (or any other Kubernetes resource). Kubernetes will read the contents of this file and create or update resources in the cluster based on the definitions provided.

So, when you run the command `kubectl create -f redis-definition.yaml`, Kubernetes will read the "redis-definition.yaml" file and create the Kubernetes resource(s) defined in that file. This allows you to deploy and manage applications and infrastructure in your Kubernetes cluster based on the configurations specified in the YAML file.

Keep in mind that this command can be used to create or update various types of Kubernetes resources, depending on what is defined in the YAML file. The specific resource type and behavior are determined by the content of the YAML file.


Verify the work by running kubectl get command :-

`kubectl get pods`


![Screenshot from 2023-10-23 15-22-29](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/465e270a-7cc5-4263-b1b9-7430580b7db2)


# Now change the image on this pod to redis.


Once done, the pod should be in a running state.

CheckCompleteIncomplete
Name: redis

Image name: redis

Use the kubectl edit command to update the image of the pod to redis.

kubectl edit pod redis
If you used a pod definition file then update the image from redis123 to redis in the definition file via Vi or Nano editor and then run kubectl apply command to update the image :-

kubectl apply -f redis-definition.yaml 

