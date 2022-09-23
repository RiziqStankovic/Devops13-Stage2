# KUBERNETES

![img](assets/kube.jpg)

Master Node
Master node adalah server utama yang mengatur semua operasi cluster menggunakan tiga komponen, yaitu kube-apiserver, kube-controller-manager, kube-scheduler dan etcd.

Di bawah ini adalah penjelasan fungsinya:

kube-apiserver: validasi dan konfigurasi data untuk objek API, yaitu pod, services, volume, dan lainnya.
kube- controller-manager: melakukan monitor cluster agar sesuai dengan konfigurasi data objek di dalam node.  
kube-scheduler: menambah objek baru ke node. Misalnya, menginstall pod ke node tertentu.
Etcd: ruang penyimpanan key value konfigurasi data cluster.
Worker Node
Worker node adalah semua server non master yang berfungsi untuk menjalankan dua komponen, yaitu kubelet dan kube-proxy. Begini penjelasan fungsi komponennya:

Kubelet: komponen untuk memastikan kontainer beroperasi di dalam objek Pod.
Kube-proxy: memelihara network rules dan meneruskan koneksi ke suatu host.
Docker image: file dari aplikasi Docker yang berfungsi untuk membuat kontainer. 

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

```
git clone https://github.com/toolkeet/dumbways-docker-microservices.git
```

kmudian deploy masuk ke direc micro nya 

```
kubectl apply -f kubernetes.yml
```

![img](assets/deploy%20simple%20app.png)

berhasil namun masih terjadi erorr di scale nya 
note crashloop

![img](assets/deployapp-erorr.png)



<!-- ![img](assets) -->