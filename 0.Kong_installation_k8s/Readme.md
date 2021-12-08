```
kubectl create -f https://bit.ly/kong-k8s-postgres



```


### kustomize 설치
```
curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh" | bash
sudo mv kustomize /usr/local/bin/
kustomize version
```



### k8s installation

kubeadm init  --apiserver-advertise-address=0.0.0.0 --pod-network-cidr=192.168.0.0/16  --apiserver-cert-extra-sans=10.1.1.10,133.186.244.173

## worker 노드
sudo mkdir /etc/docker
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

sudo systemctl enable docker
sudo systemctl daemon-reload
sudo systemctl restart docker

# kubelet가 실행인지 확인
sudo systemctl status kubelet
# 실행중이 아닐 경우
sudo systemctl start kubelet




kubeadm init   --apiserver-advertise-address=192.168.75.150  --pod-network-cidr=10.244.0.0/16

kubeadm join 192.168.75.150:6443 --token zxxunl.abrlu0ii3bvgb0mm \
        --discovery-token-ca-cert-hash sha256:bd45d86d1f26e9064dc220c027b9ed11bf46207e78c3419a9f655ea663d22486

kubeadm init  --apiserver-advertise-address=0.0.0.0 --pod-network-cidr=10.244.0.0/16  --apiserver-cert-extra-sans=10.1.1.10,133.186.244.173

kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml


kubeadm join 192.168.0.5:6443 --token 4dgxlf.fart6sm64523086j \
        --discovery-token-ca-cert-hash sha256:e4978cb8b10b3fbd657422eb744fabad03898d0088a1ee46c0ebb13362426d15
