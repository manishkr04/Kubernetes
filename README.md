# Kubernetes
Learning and Implementing Kubernetes

### Installing minikube (Local Kubernetes)
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

To Start minikube it require a Docker as Driver (or a virtual machine), So we have to install Docker 
### Install using the apt repository
#### Set up Docker's apt repository.

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

#### Install the Docker packages
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### Verify that the Docker Engine installation is successful by running the hello-world image.
```bash
sudo docker run hello-world
```

#### Giving Perminssion to Docker by adding docker to present User Group and new group docker
```bash
sudo usermod -aG docker $USER && newgrp docker
```

Now You can start minikube

#### Starting minikube
```bash
minikube start --driver=docker
```

#### Installing kubectl --classic 
- Kubectl is a command-line tool used to manage and interact with Kubernetes clusters for deploying and monitoring applications
```bash
sudo snap install kubectl --classic
```

#### List all the Pods across all namespaces
```bash
$ kubectl get po -A

$ minikube status
# checks the status of the Minikube cluster, displaying information about the cluster's components such as the VM, Kubernetes, and any running services.

$ kubectl get node
#retrieves information about the nodes in the Kubernetes cluster, listing their status, roles, and other relevant details.
```
