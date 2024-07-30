Follow the steps until the kubeadm install:
  - <https://v1-29.docs.kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/>
  - Install a specific version:
    - `sudo apt-get install kubelet=1.30.0-1.1 kubeadm=1.30.0-1.1 kubectl=1.30.0-1.1`

- Make sure that Swap is disabled:
  - `swapoff -a`

- Init Master Node:
```
kubeadm init \
  --pod-network-cidr=10.244.0.0/16 \
  --apiserver-advertise-address=192.168.2.53
```

Output:
```
...
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.2.53:6443 --token lrz5du.pqn77s83jpm2eyui \
	--discovery-token-ca-cert-hash sha256:d0a6627a9611f92f98093436a3242ee7a30baf13414b2079cbbe8479bc2e4304
```

K8s Network:
  - Using Flannel:
    - `k apply -f kube-flannel.yml`    
  - After the Nodes will be Ready.