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






