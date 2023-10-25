# How many Services exist on the system?
![Screenshot from 2023-10-25 06-40-01](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/3e7d64e6-d605-48b8-bf88-f3c8988c8ac4)

# That is a default service created by Kubernetes at launch.

![Screenshot from 2023-10-25 06-40-01](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/3e7d64e6-d605-48b8-bf88-f3c8988c8ac4)

# What is the type of the default kubernetes service?
Run the command: kubectl get service and look at the Type column.

![Screenshot from 2023-10-25 06-40-01](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/3e7d64e6-d605-48b8-bf88-f3c8988c8ac4)

# What is the targetPort configured on the kubernetes service?

Run the command: kubectl describe service and look at TargetPort.

![Screenshot from 2023-10-25 06-44-18](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/6d9c3f9f-739f-4097-94e6-68f64ab78b34)


# How many labels are configured on the kubernetes service?

Run the command: kubectl describe service and look at the Labels.

![Screenshot from 2023-10-25 06-44-18](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/6d9c3f9f-739f-4097-94e6-68f64ab78b34)


# How many Endpoints are attached on the kubernetes service?
Run the command: kubectl describe service and look at the Endpoints.

![Screenshot from 2023-10-25 06-44-18](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/6d9c3f9f-739f-4097-94e6-68f64ab78b34)

# How many Deployments exist on the system now?

![Screenshot from 2023-10-25 06-49-43](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/dea1a300-db63-4d6a-a230-4df8b5e65fa5)

# What is the image used to create the pods in the deployment?
Run the command: kubectl describe deployment and look under the containers section.

![Screenshot from 2023-10-25 06-51-20](https://github.com/Althaf-official/KodeKloud_Kubernetes/assets/105126131/7bb697a2-17fd-461a-aa89-d5ce3d7b22a0)

