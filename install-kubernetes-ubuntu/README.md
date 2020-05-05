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

### STEP FOUR:
Your Kubernetes control-plane has initialized successfully!
To start using your cluster, you need to run the following as a regular user:


 ```
  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### Step FIVE:
now run following commands 

```
 kubectl get nodes
```
it will return following and as you can see status is notReady.the reason is network plugin is not installed. in order to install network plugin proceed to step SIX

```
NAME          STATUS     ROLES    AGE   VERSION
srvrmaster     NotReady   master   26m   v1.18.2
nodeslave0    NotReady     <none>   22m   v1.18.2
knodeslave1   NotReady   <none>   22m   v1.18.2
```

### Step SIX:
in order to install network pluging excute following command

```
kubectl apply -f https://docs.projectcalico.org/v3.11/manifests/calico.yaml
```

here we are using Calico there are other options available, read more [Here]( https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#pod-network)

