# course

## Google Cloud

`gcloud config set project kubernetes-wildlife`

`gcloud config set compute/zone us-west1-a`

`gcloud container clusters create wildlife`

```
NAME      LOCATION    MASTER_VERSION  MASTER_IP       MACHINE_TYPE   NODE_VERSION    NUM_NODES  STATUS
wildlife  us-west1-a  1.14.10-gke.27  35.199.164.233  n1-standard-1  1.14.10-gke.27  3          RUNNING
```

`gcloud container clusters delete wildlife`

`gcloud container clusters get-credentials wildlife`

`gcloud compute firewall-rules create nginx-node-port --allow tcp:<nodePort>`

`gcloud compute firewall-rules delete nginx-node-port`

## Application 

1- Only one rng per node.

### Start

`kubectl create deployment redis --image=redis`

`kubectl create deployment hasher --image=dockercoins/hasher:v0.1`

`kubectl create deployment rng --image=dockercoins/rng:v0.1`

`kubectl create deployment webui --image=dockercoins/webui:v0.1`

`kubectl create deployment worker --image=dockercoins/worker:v0.1`

`kubectl expose deploy/redis --port=6379 (ClusterIP for default)`

`kubectl expose deploy/rng --port=80`

`kubectl expose deploy/hasher --port=80`

`kubectl expose deploy/webui --type=NodePort --port=80`

`kubectl scale deploy/worker --replicas=3`

### Clean

`kubectl delete deploy/redis`

`kubectl delete deploy/hasher`

`kubectl delete deploy/rng`

`kubectl delete deploy/webui`

`kubectl delete deploy/worker`

### Commands

`kubectl get deploy/rng`

`kubectl get deploy/rng -o yaml --export > rng.yml`

`kubectl apply -f rng.yaml`

`kubectl get daemonsets.apps`

`kubectl get services`

`kubectl logs deploy/worker`

`kubectl exec worker-598788db65-2wvp2 -it /bin/sh`

### helm

`helm create dockercoins`

```
while read kind name; do
kubectl get -o yaml --export $kind $name > templates/$name-$kind.yaml
done <<EOF
deployment worker
deployment hasher
daemonset rng
deployment webui
deployment redis
service hasher
service rng
service webui
service redis
EOF
```

`helm install -n dockercoins dockercoins ./`
 
`helm upgrade -n dockercoins -f values.yaml dockercoins ./`





