# KUBERNETES

# Kubernetes Installation




![img](assets/kube1.png)
![img](assets/kube2.png)
```
ufw disable
```

![img](assets/kube3.png)
```
swapoff -a; sed -i '/swap/d' /etc/fstab
```
```
cat >>/etc/sysctl.d/kubernetes.conf<<EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
```
```
sysctl --system
```

![img](assets/kube4.png)
```
cat <<EOF | sudo tee /etc/docker/daemon.json
{
"exec-opts": ["native.cgroupdriver=systemd"],
"log-driver": "json-file",
"log-opts": {
"max-size": "100m"
},
"storage-driver": "overlay2"
}
EOF
```

![img](assets/kube5.png)
```
sudo systemctl enable docker
sudo systemctl daemon-reload
sudo systemctl restart docker
```
![img](assets/kube6.png)
```
sudo apt-get update && sudo apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
sudo apt-get update
```
![img](assets/kube7-erorr.png)
```
sudo apt-get install -y kubelet kubeadm kubectl kubernetes-cni
```
```
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```
![img](assets/kube7-testing.png)
```
kubeadm init
```
![img](assets/kube7.png)
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

![img](assets/kube8-erorr.png)
```
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.24.1/manifests/calicoctl-etcd.yaml

```

![img](assets/kube10-%20calico.png)
```
kubectl get pods --all-namespaces
```
```
kubeadm token create --print-join-command
```
```
kubectl get nodes
```
![img](assets/kube11-.png)
```

```

# Deploy Nginx

![img](assets/kubesuce.png)


![img](assets/kube9-init.png)
```
kubectl create deploy nginx --image nginx
```
```
kubectl expose deploy nginx --port 80 --type NodePort
```
```
kubectl get svc
```

```
kubectl describe pod nama pod
```

![img](assets/kube9.png)



![img](assets/kubedeploy.png)


# Deploy App

disini saya akan deploy simple app micro services


![img](assets/deploy%20simple%20app.png)

berhasil namun masih terjadi erorr di scale nya 
note crashloop

![img](assets/deployapp-erorr.png)



<!-- ![img](assets) -->