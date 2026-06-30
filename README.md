# Pyshape

This repository contains all the materials that is required for the assignment with everything explained step by step

---

## Step-1:  Install Minikube and other tools with some configuration (If not using cloud provided kubernetes service such as AKS/GKE/EKS)

```bash
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```
**Start Minikube**
```
minikube start
```
**Install kubectl to intract with kubernetes cluster**
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" 
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
```
kubectl rollout restart deployment coredns -n kube-system
```
