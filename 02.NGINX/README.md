### /etc/nginx/conf.d/default.conf
- 컨테이너 안의 해당 위치에 존재


```
#add test part
server {
	server_name		localhost;
	listen			6081; #포ㅡ 설정
	listen			192.168.75.149:6081; # haproxy를 받기 위해


	# OCP ocp4 v4.6.17 API Proxy
	location /vnc_auto.html {
		proxy_pass http://192.168.63.100:6080 #해당 url로 넘김.
		proxy_set_header X-Real-IP $remote_addr; 
        
        proxy_http_version 1.1;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header Host $http_host;
		proxy_set_header Sec-WebSocket-Protocol $arg_protocol;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection $connection_upgrade;
		proxy_set_header Authorization "Bearer $arg_access_token";
		proxy_set_header Origin "*";
	}

}

```
- `proxy_set_header X-Real-IP $remote_addr;` : 실제 접속자의 IP를 X-Real-IP 헤더에 입혀서 전송 


```
#Websocket 필수 설명
location /socket {
    proxy_pass http://sockets;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
}
```

```
# Web-socket 관련 설정들

# 1. HTTP/1.1 버전에서 지원하는 프로토콜 전환 메커니즘을 사용한다
proxy_http_version 1.1;

# 2. hop-by-hop 헤더를 사용한다
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
# 3. 받는 대상 서버(WAS)
proxy_set_header Host $host;
```