// curl --location -g --request POST 'http://192.168.63.100:5000/v3/auth/tokens' --header 'Content-Type: application/json' --data @osp_data.json


1. curl -i $PROXY_IP/test_osp  --location -g --request POST 'http://192.168.63.100:5000/v3/auth/tokens' --header 'Content-Type: application/json' --data @osp_data.json
    - 172.17.0.1 - - [09/Nov/2021:06:10:49 +0000] "POST /test_osp HTTP/1.1" 201 10132 "-" "curl/7.61.1"
2021/11/09 06:10:49 [error] 1098#0: *551121 [lua] batch_queue.lua:187: entry batch was already tried 10 times, dropping it, context: ngx.timer, client: 172.17.0.1, server: 0.0.0.0:8000

2. curl -i $PROXY_IP/test_osp -X POST --header 'Content-Type: application/json' --data @osp_data.json



