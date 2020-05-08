# minikube
 
## minikube start

Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM.

# kubernetes

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

## Volumes

`kubectl port-forward nginx-with-volume 8080:80`

## Namespaces

`kubectl get ns`

`kubectl get ns -o yaml`

`kubectl config get-contexts`

`kubectl config set-context --current --namespace=kube-node-lease`

## Security

1- TLS

2- Token

3- Username / password

4- Proxy

RBAC = Role Base Access Control

`kubectl get serviceaccounts`

`kubectl get serviceaccounts default -o json`

`kubectl get secret default-token-z5fcr -o json`

`kubectl create serviceaccount viewer`

`kubectl get serviceaccount viewer -o yaml`

`kubectl get clusterrole`

`kubectl get clusterrole view -o yaml`

`kubectl create rolebinding viewercanview --clusterrole=view --serviceaccount=default:viewer`

`SECRET=$(kubectl get sa viewer -o json | jq -r '.secrets[0].name')`

`TOKEN=$(kubectl get secret $SECRET -o json | jq -r '.data.token' | base64 --decode)`

`kubectl auth can-i create pods`

`kubectl auth can-i list pods --namespace default --as viewer`

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

## Configuration

1- Arguments  

2- Environment variables

3- Configuration file

`kubectl create configmap haproxy --from-file=haproxy.cfg`

`kubectl get configmaps`

`kubectl get configmap haproxy -o yaml`

`kubectl edit configmap haproxy`

`kubectl create configmap registry --from-literal=http.addr=0.0.0.80`

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

`kubectl create namespace dockercoins`

