- upstream 으로 넣기 ->target으로 만약에 IP가 다르더라도 포트별로 같은 서비스이면 
    - https://docs.konghq.com/kubernetes-ingress-controller/2.0.x/guides/using-rewrites/
- 같은 IP별로 같은 서비스이면

`curl $PROXY_IP/osp/5000/v3/auth/tokens -X POST --header 'Content-Type: application/json' --data @osp_data.json -i`


- `kubectl patch -n echo service echo -p '{"metadata":{"annotations":{"konghq.com/path":"/api"}}}'`
    - 해당 서비스는 쓰는 ingress는 /api/URL이 된다.
```
  annotations:
    konghq.com/strip-path: "false"
```
    - ingress에 꼭 추가하기

#TEST
- KongIngress test
kubectl patch service echo -p '{"metadata":{"annotations":{"konghq.com/override":"demo-customization"}}}'
service/echo patched
 - 서비스에 추가 가능!

 link: https://docs.konghq.com/kubernetes-ingress-controller/2.0.x/guides/using-kongingress-resource/#main