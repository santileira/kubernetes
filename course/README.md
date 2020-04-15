# course

### kubectl create deployment redis --image=redis

### kubectl create deployment hasher --image=dockercoins/hasher:v0.1

### kubectl create deployment rng --image=dockercoins/rng:v0.1

### kubectl create deployment webui --image=dockercoins/webui:v0.1

### kubectl create deployment worker --image=dockercoins/worker:v0.1

### kubectl logs deploy/worker

### kubectl exec worker-598788db65-2wvp2 -it /bin/sh

### kubectl expose deployment redis --port 3679 (ClusterIP for default)

### kubectl delete pods worker-598788db65-2wvp2

### kubectl expose deployment rng --port 80

### kubectl expose deployment hasher --port 80

### kubectl expose deploy/webui --type=NodePort --port=80

### kubectl get svc

### kubectl scale deploy/worker --replicas=3

### kubectl get deploy/rng -o yaml --export >rng.yaml

### kubectl apply -f rng.yaml

### kubectl get daemonsets.apps