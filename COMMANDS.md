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

## ConfigMap

`kubectl create configmap haproxy -from-file=haproxy.cfg`

`kubectl get configmaps`

`kubectl get configmaps haproxy -o yaml | less`

`kubectl apply -f ./haproxy.yaml  `

## Rolling updates

`kubectl set image deploy worker worker=dockercoins/worker:v0.2`

`kubectl rollout undo deploy worker`

`kubectl rollout status deploy worker`

## Liveness

The kubelet uses liveness probes to know when to restart a container

Commands:

1- Exec
2- httpGet
3- tcpSocket

## Readiness

The kubelet uses readiness probes to know when a container is ready to start accepting traffic

Commands:

1- httpGet
2- tcpSocket

## Startup

The kubelet uses startup probes to know when a container application has started.

# helm

## Repositories

1- Chart museum

2- S3

3- Git

## Commands

`helm repo add stable https://kubernetes-charts.storage.googleapis.com/`

`helm search repo stable/prometheus`

`helm inspect chart stable/prometheus`

`helm install --set server.service.type=NodePort --set server.persistentVolume.enabled=false prometheus stable/prometheus`

`helm status prometheus`

`helm list`

`helm uninstall prometheus`

`helm create dockercoins`