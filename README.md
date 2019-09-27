# kubernetes
Tutorial about kubernetes

## What is container orchestrators?

Container orchestrators are tools which group systems together to form clusters where containers' deployment and management is automated at scale while meeting the following requirements:

- Fault-tolerance.

- On-demand scalability

- Optimal resource usage

- Auto-discovery to automatically discover and communicate with each other

- Accessibility from the outside world

- Seamless updates/rollbacks without any downtime.

## What is Kubernetes?

Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.

## Hardware

### What is a node?

A node is the smallest unit of computing hardware in Kubernetes. It is a representation of a single machine in your cluster. In most production systems, a node will likely be either a physical machine in a datacenter, or virtual machine hosted on a cloud provider like Google Cloud Platform.

### What is a cluster?

A cluster is a pool of nodes

### What is the persistent volumes?

Because programs running on your cluster aren’t guaranteed to run on a specific node, data can’t be saved to any arbitrary place in the file system. If a program tries to save data to a file for later, but is then relocated onto a new node, the file will no longer be where the program expects it to be. For this reason, the traditional local storage associated to each node is treated as a temporary cache to hold programs, but any data saved locally can not be expected to persist.

## Software

### What is a pod?

Kubernetes does not run containers directly; instead it wraps one or more containers into a higher-level structure called a pod
Any containers in the same pod will share the same resources and local network. Containers can easily communicate with other containers in the same pod as though they were on the same machine while maintaining a degree of isolation from others.

## What is a Deployment?

Deployments represent a set of multiple, identical Pods with no unique identities. A Deployment runs multiple replicas of your application and automatically replaces any instances that fail or become unresponsive. In this way, Deployments help ensure that one or more instances of your application are available to serve user requests. Deployments are managed by the Kubernetes Deployment controller.

## Tools

- kubernetes-cli (kubectl) 
- minikube (Minikube is a tool that makes it easy to run Kubernetes locally)
