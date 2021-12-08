## 권고 사항
Prerequisites
A Kubernetes cluster, v1.19 or later
kubectl v1.19 or later
(Enterprise only) A license.json file from Kong


## Kong 설치
- DB less
kubectl apply -f https://bit.ly/k4k8s
service -> NodePort로 변경
- 마지막: test
curl -i kong-proxy가 존재하는 node의 ip:kong-proxy 포트


## Service 테스트 하기
