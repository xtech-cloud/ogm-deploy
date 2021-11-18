# Develop
微服务容器只包含ogm-sandbox,需要在sandbox中运行微服务。

```bash
docker-compose -f ./docker-compose-dev.yml up -d
```

- WSL2额外设置
如果docker运行在wsl2中，本机可以用localhost访问容器的端口，但是外网无法访问。如果希望外网也能正常访问，需要在powershell中做端口转发，方法如下:
```
netsh interface portproxy add v4tov4 listenport=80 listenaddress=0.0.0.0 connectport=80 connectaddress=localhost
netsh interface portproxy show all
```

# Mini
包含已发布的微服务容器。

```bash
docker-compose -f ./docker-compose-mini.yml up -d
```

# Small

## SRC

克隆ogm-docker到/data/ogm
```bash
cd /data/ogm
docker-compose -f ./docker-compose-small-src.yml up -d
chmod -R 777 ./etcd
docker restart ogm_etcd_1
```

## DSC

克隆ogm-docker到/data/ogm
```bash
cd /data/ogm
docker-compose -f ./docker-compose-small-dsc.yml up -d
```

## MSA

克隆ogm-docker到/data/ogm
```bash
cd /data/ogm
docker-compose -f ./docker-compose-small-msa.yml up -d
```

## VPP

克隆ogm-docker到/data/ogm
```bash
cd /data/ogm
docker-compose -f ./docker-compose-small-vpp.yml up -d
```

## PMC

克隆ogm-docker到/data/ogm
```bash
cd /data/ogm
docker-compose -f ./docker-compose-small-pmc.yml up -d
```
