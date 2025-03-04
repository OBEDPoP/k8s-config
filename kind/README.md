## Install kind on linux:
use it as test env alone, strictly not for production usecase

# K + in + d = Kind

# K - Kubernetese
# In - In
# D - Docker
Hence kubernetese is deployed within docker



create a directory ``` 
~/kind ```

create a sh file and add below data ``` 
vi kind.sh```


```

#!/bin/bash

sudo apt-get update -y

sudo apt-get install docker.io -y

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.26.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

echo "kind & kubectl Successfully Installed!"

```

give executable access to the file ``` 
chmod +x kind.sh ```

KUBECTL, Docker and KIND installed!!....

give Docker access to run commands ``` 
sudo usermod -aG docker Username && newgrp docker ```

create config.yaml

```
kind: cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
    image:  kindest/node:v1.32.1
  -role: worker
    image:  kindest/node:v1.32.1
  -role: worker
    image:  kindest/node:v1.32.1
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: tcp

```
run below command to create cluster
```
kind create cluster --name=my-first-cluster --config=config.yaml

kubectl cluster-info --context my-first-cluster

kubectl get nodes

kubectl get all
```


## Multi-node clusters

You can also have a cluster with multiple control-plane & worker nodes, create a config file.

```

kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  image: kindest/node:v1.32.1
- role: worker
  image: kindest/node:v1.32.1
- role: worker
  image: kindest/node:v1.32.1
- role: worker
  image: kindest/node:v1.32.1
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: tcp

```


![Screenshot 2025-01-28 155902](https://github.com/user-attachments/assets/addf89a1-9316-4781-8178-1f3942eb87d9)

