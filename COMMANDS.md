# minikube

## minikube start

Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM.

## Pods

### kubectl get pods pingpong-c849c8bbc-vrd2s -o yaml | less

### kubectl get pods -o wide

### kubectl get pods -w (watch)

### kubectl run --restart=Never sleep --image=busybox sleep 20;

### kubectl run --dry-run -o yaml pingpong --image=alpine ping 1.1.1.1

### kubectl run --dry-run -o yaml pingpong --image=alpine ping 1.1.1.1 | kubectl apply -f -

### kubectl delete pod sleep

### kubectl logs pingpong-c849c8bbc-vrd2s --follow

## Deployments

### kubectl get deploy

### kubectl create deployment nginx --image=nginx

### kubectl get deploy/nginx

### kubectl get deploy/nginx -o yaml

### kubectl scale deploy/nginx --replicas=8 

### kubectl delete deploy pods

## Services

### ClusterIP 

Only reachable form within the cluster

### NodePort

Exposes the Service on each Node`s IP as static port. qqqYou have to create a firewall rule to allow the traffic.

#### kubectl expose deploy/nginx --type=NodePort --port=80

#### kubectl get service/nginx -o yaml | less

#### kubectl get nodes -o wide

### LoadBalancer

Exposes the service externally using a cloud provider's load balancer.

#### kubectl expose deploy/nginx --type=LoadBalancer --port=80

### ExternalName

Maps the service to the contents of the externalName field but returning a CNAME record with its value.

## DaemonSet

DaemonSets are used when you want to make sure that a particular pod runs on all nodes that belong to a cluster.

`kubectl apply -f rng.yml`

`kubectl apply -f rng.yml -validate=false`

`kubectl get daemonsets.apps`

## Labels

`kubectl get pods --selector=app=webui`

`kubectl label pod rng-wed app-`

## Endpoints

`kubectl get endpoints`