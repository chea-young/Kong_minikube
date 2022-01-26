# Kong_minikube

1. [O] Minikube 설치하기 
2. [O] Kong 설치하기 
3. [O] Kong UI (Konga 설치하기) 
    - kong-admin 설치하기
    - konga 설치하기
4. [O] 라우터 테스트 
5. [O] Plugin 테스트   
6. [O] 라우트 분기 테스트 
    - 유료버전을 쓰거나
    - Customize 된 plugin 사용시 가능(하지만 일정한 kong 버전에서만 사용 가능)
8. [O] Elasticsearch, Kibana, logstash 연결하기 
9. [O] req/res 로그를 엘라스틱 서치로 테스트 하기 
10. [O] req 메세지에서 요청자 정보 확인하기

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
