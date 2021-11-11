```

$ kubectl create deployment source-ip-app --image=k8s.gcr.io/echoserver:1.4 -n kong

$ kubectl patch svc kong-proxy -n kong -p '{"spec":{"externalTrafficPolicy":"Local"}}' #defalut 는 Cluster
$ kubectl get svc kong-proxy -n kong -o yaml | grep -i healthCheckNodePort // 변경 확인 ->Local일 때만 존재
// healthCheckNodePort: 30924 
// 출력은 이와 비슷하게 나와야 한다.

$ curl localhost:30924/healthz // /healthz는 앤드포인트를 가져오는데 사용
```

- 정리하기
    - 설정 방법
    - 설정한 것 확인
    - 변경 확인 (+원래는 이랬는데 변경하니 이렇게 나오게 되었다.) 
     + 원인은 이거였다.