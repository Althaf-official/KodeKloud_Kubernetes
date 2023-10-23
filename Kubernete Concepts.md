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










