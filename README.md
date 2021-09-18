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

# Small

## SRC

```bash
docker-compose -f ./docker-compose-small-src.yml up -d
```

## DSC

```bash
docker-compose -f ./docker-compose-small-dsc.yml up -d
```
