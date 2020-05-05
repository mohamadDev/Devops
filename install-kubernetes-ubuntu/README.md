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


```
sudo apt-get update && sudo apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```

