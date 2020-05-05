# install kubernetes on ubuntu 



### Step ZERO:  
make sure all nodes can see  eachother 

### step ONE: 
You will run these commands on all of your machines:

```
sudo apt-get update 
sudo apt-get install docker.io
```

### Step TWO 
Installing kubeadm, kubelet and kubectl
You will install these packages on all of your machines:

#### kubeadm: 
the command to bootstrap the cluster.

#### kubelet: 
the component that runs on all of the machines in your cluster and does things like starting pods and containers.

#### kubectl: 
the command line util to talk to your cluster.


### Step THREE 
Initialize cluster


```
kubeadm init --apiserver-advertise-address={{MA.STER.IP.ADDR}}  --pod-network-cidr=192.168.0.0/16
```
command above may take few minutes and in return it gives you a token by which you can append new nodes to your cluster. excute it in any other node that you would like to join to your cluster
 
 ```
kubeadm join MA.STER.IP.ADDR:6443 --token ce#####n.########## \
    --discovery-token-ca-cert-hash sha256:6#######3f8a#################f##########3
```
