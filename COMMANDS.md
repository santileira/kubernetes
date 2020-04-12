# minikube

## minikube start

Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM.

## kubectl cluster-info

View the cluster details.

## kubectl get nodes

This command shows all nodes that can be used to host our applications.

## deploy app on Kubernetes

`kubectl run kubernetes-bootcamp --image=<url-image> --port=<port>`

ex: `kubectl run kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1 --port=8080`

## kubectl get deployments

List our deployments

## run the proxy

The kubectl command can create a proxy that will forward communications into the cluster-wide, private network

`kubectl proxy`

## kubectl get pods

`curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/`

## kubectl get

List resources

## kubectl describe

Show detailed information about a resource

## kubectl logs

Print the logs from a container in a pod

## kubectl exec

Execute a command on a container in a pod

## kubectl logs $POD_NAME

View the container logs

## kubectl exec $POD_NAME env

List the environment variables.

## kubectl exec -ti $POD_NAME bash

## kubectl get pods pingpong-c849c8bbc-vrd2s -o yaml | less

## kubectl get pods -o wide 

## kubectl logs pingpong-c849c8bbc-vrd2s --follow

## kubectl get replicasets.apps

## kubectl delete pods pingpong-c849c8bbc-vrd2s

## kubectl scale deploy/pingpong --replicas=8