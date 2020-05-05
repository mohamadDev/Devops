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

