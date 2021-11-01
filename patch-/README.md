1. patch-*.yml 파일 작성
2. `kubectl patch deploy -n kong ingress-kong --patch-kong-deployment.yml`
3. `kubectl patch service -n kong kong-proxy --patch-file=patch-kong-service.yml`
4. tcp-ingress.yml 작성
5. kubectl apply --- 커맨드 치기
6. `psql -h $PROXY_IP -p 11111 -U kong` 하면 연결된다