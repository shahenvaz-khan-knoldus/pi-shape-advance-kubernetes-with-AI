# Pyshape

This repository contains all the materials that is required for the assignment with everything explained step by step


## Prequisites

- Docker must be installed in your WSL https://docs.docker.com/engine/install/ubuntu/

- Azure account with azure AI foundry setup

---

## Minikube Setup for local development: Install Minikube and other tools with some configuration (If not using cloud provided kubernetes service such as AKS/GKE/EKS)

**Download Minikube in you local machine**

```bash

curl  -LO  https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64

sudo  install  minikube-linux-amd64  /usr/local/bin/minikube && rm  minikube-linux-amd64

```

**Start Minikube**

```

minikube start

```

**Install kubectl to intract with kubernetes cluster**

```curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

```

**SSH Minikube to disable cluster domain**

```

minikube ssh

sudo vi /etc/resolv.conf

```

search this line **search domain.name** and then press i button from the Keyboard to enable editing and then comment it **#search domain.name** press Esc button and the type :wq to save the file.

  

now exit from the minikube node by typing this command

  

```

exit

```

  

**Now Restart coreDNS service**

```kubectl rollout restart deployment coredns -n kube-system```

  

## kubectl AI Setup

  

Before installing it you need to create an azure account and setup model deployment in **Azure AI foundry** service

  

**Install kubectl AI tool**

```curl -sSL https://raw.githubusercontent.com/GoogleCloudPlatform/kubectl-ai/main/install.sh | bash```

  

**Add you AZURE OPENAI Environment variables**

```export AZURE_OPENAI_ENDPOINT="replace it with actual AZURE OPENAI ENDPOINT"```

```export AZURE_OPENAI_API_KEY="replace it with AZURE OPENAI API KEY"```

  

**Run Kubectl AI**

  

```kubectl-ai --llm-provider="azopenai" --model="replace it with model name"```

  

Run some commands like

  

```

get all the deployments

get all the pods

```

## Kedify

  

- visit https://kedify.io/

- Click on Sign In button

- Click on Sign Up and enter your details

- Once Account create is done In the dashboard select Cluster option

- Then click on Connect Cluster this will provide you kubectl apply command like this

``` kubectl apply -f manifests_url```

