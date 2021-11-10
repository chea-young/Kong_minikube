- upstream 으로 넣기 ->target으로 만약에 IP가 다르더라도 포트별로 같은 서비스이면 
    - https://docs.konghq.com/kubernetes-ingress-controller/2.0.x/guides/using-rewrites/
- 같은 IP별로 같은 서비스이면

`curl $PROXY_IP/osp/5000/v3/auth/tokens -X POST --header 'Content-Type: application/json' --data @osp_data.json -i`