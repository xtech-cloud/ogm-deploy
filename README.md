# Develop

修改host

```bash
vi /etc/hosts
```

加入
```
127.0.0.1	etcd
```

安装容器

```bash
docker-compose -f ./docker-compose-dev.yml up -d
```

添加GRPC转换

```bash
curl http://127.0.0.1/apisix/admin/proto/1 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1' -X PUT -d '
{
    "content" : "
syntax = \"proto3\";
package xtc.ogm.startkit;
service Healthy
{
    rpc Echo(Request) returns (Response) { }
}
message Request { string msg = 1; }
message Response { string msg = 1; }
"
}'

curl http://127.0.0.1/apisix/admin/routes/111 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1' -X PUT -d '
{
    "methods": ["POST"],
    "uri": "/xtc/ogm/startkit/Healthy/Echo",
    "plugins": {
        "grpc-transcode": {
         "proto_id": "1",
         "service": "xtc.ogm.startkit.Healthy",
         "method": "Echo"
        }
    },
    "upstream": {
        "scheme": "grpc",
        "type": "roundrobin",
        "nodes": {
            "10.1.100.11:18899": 1
        }
    }
}'

```

测试
```bash
curl -i -X POST -H "Content-Type:application/json" http://127.0.0.1/xtc/ogm/startkit/Healthy/Echo -d '{"msg":"hello"}'
```
