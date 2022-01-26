# Kong_minikube

1. [x] Minikube 설치하기 
2. [x] Kong 설치하기 
3. [X] Kong UI (Konga 설치하기) 
    - kong-admin 설치하기
    - konga 설치하기
4. [X] 라우터 테스트 
5. [X] Plugin 테스트   
6. [X] 라우트 분기 테스트 
7. [X] req/res 로그를 엘라스틱 서치로 테스트 하기 
8. [X] req 메세지에서 요청자 정보 확인하기

## Ingress using Kong
 - Dynamic configuration
    - Quickly responds to changes in infrastructure
    - No expensive process reloads
 - Pluggable architesture
    - Authentication
    - Observability via logging, metrics, tracing
    + 로드밸런싱 등 플러그를 통해 다양한 기능을 구현할 수 있다. 
 - Transition to microservices
    - Break monoliths piece by piece
 - NGINX core
    - Battle tested

## Kong - K8s
- kong ingress controller will listen to eery k8s event and it will react to those events that he that have been specified into the k8s the cardiff config and it will automatically configure and add or remove target parts from the conch upstream and target data model right so what you do we're gonna see it's running you know
