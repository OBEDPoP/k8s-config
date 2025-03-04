## Minikube install on linux:

use it as test env in your local, strictly not for production usecase
```

sudo apt-get update -y

sudo apt-get install docker.io -y

curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

### Start Cluster

```
minikube start --driver=docker --vm=true
```
![Screenshot 2025-01-28 160559](https://github.com/user-attachments/assets/3f14cdfb-a006-468c-916f-278f43041d1e)
