----E
## `kubectl appiy -f elasticsearch.yaml -n kong`

`$curl http://$(minikube ip):30482 # 30005: svc/es-manual port`

[root@control-plane ELK]# curl -i 192.168.50.160:30482
HTTP/1.1 200 OK
content-type: application/json; charset=UTF-8
content-length: 558

{
  "name" : "elasticsearch-7474cd8c7-w9t9g",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "VMwyWr1dTHO2MjzpeoPuxg",
  "version" : {
    "number" : "7.8.0",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "757314695644ea9a1dc2fecd26d1a43856725e65",
    "build_date" : "2020-06-14T19:35:50.234439Z",
    "build_snapshot" : false,
    "lucene_version" : "8.5.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}


---키바나
$kubectl create deployment kib-manual --image kibana:7.8.0 -n kong

kubectl set env deployments/kib-manual -n kong ELASTICSEARCH_HOSTS=http://$(minikube ip):30560

kubectl expose deployment kib-manual --type NodePort --port 5601 -n kong # 서비스 생성 키바나

http://192.168.50.160:31935/status # 키바나 대시보드 확인

--------Logstash

$ kubectl create configmap log-manual-pipeline \
--from-file ./logstash.conf -n kong

[Output]
configmap/log-manual-pipeline created

#deployment 다운 -> L-delployment 복붙

[Output]
deployment.apps/log-manual created

$ kubectl logs –f log-manual-5c95bd7497-ldblg
- 확인 시 "No Available Connections” to the Elasticsearch instance endpoint with the URL http://elasticsearch:9200/." 가 나와도 문제가 되지 않는다.

[root@control-plane ELK]#  kubectl expose deployment log-manual --type NodePort --port 5044 -n kong

service/log-manual exposed



### 참고사이트: 
- https://lahuman.github.io/kubernetes-logging/
- https://coralogix.com/blog/elasticsearch-logstash-kibana-on-kubernetes/