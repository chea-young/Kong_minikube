```
https://emptyreset.tistory.com/31 #테스트 부터 참고

https://engineeringcode.tistory.com/125 # 설치 참고

```

# nano /etc/haproxy/haproxy.cfg
```
# 유효성 검사
haproxy -f /etc/haproxy/haproxy.cfg
haproxy -f /etc/haproxy/haproxy.cfg -c

systemctl restart haproxy

#확인
watch -d "netstat -an | grep \":30081\""

firewall-cmd --reload
firewall-cmd --list-all
```

## haproxy 
#### 1 경우
[https://m.blog.naver.com/wideeyed/221856790984]
`acl <aclname> <criterion>[,<converter>] [flags] [operator] [<pattern>] ...`

```
frontend api_gateway
    bind *:8881
    acl PATH_aa path_beg -i /aa #접두어가 /aa이면 PATH_aa의 경우로
    acl PATH_bb path_beg -i /bb
    use_backend be_aa if PATH_aa # PATH_aa 이면 be_aa 할당
    use_backend be_bb if PATH_bb
	default_backend be_etc

backend be_aa
    server server1 host.docker.internal:9991 check #server  server2 192.168.60.161:80 check

backend be_bb
    server server1 host.docker.internal:9992 check

backend be_etc
    server server1 host.docker.internal:9993 check
```
- path_beg 옵션은 prefix match로 URL의 접두사가 일치하는지만 검사

```
frontend https_frontend
    ...
    acl is_websocket path_beg /
    acl is_websocket hdr(Upgrade) -i WebSocket
    acl is_websocket hdr_beg(Host) -i ws
    use_backend websockets if is_websocket
```
hdr(Upgrade) -i WebSocket
- Upgrade 헤더가 포함되어 있다면 WebSocket 오퍼레이터를 지정

acl is_websocket hdr_beg(Host) -i ws
- hdr_beg(Host)는 요청 Host가 ws로 시작할 경우