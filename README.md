# Develop

安装容器

```bash
docker-compose -f ./docker-compose-dev.yml up -d
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
