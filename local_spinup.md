# 本地环境搭建

## 安装Golang,设置GOPATH环境变量

## 安装 [Micro](https://github.com/micro/micro)

```bash
go get -u github.com/micro/micro
go get -u github.com/micro/go-micro
```

## 安装Consul

可直接执行

```bash
docker-compose up
```

## 下载相应微服务

```bash
git clone git@github.com:ilovelili/dongfeng-core.git
git clone git@github.com:ilovelili/dongfeng-core-proxy.git
```

## 本地安装Go package

在 `dongfeng-core` 根目录下执行

```bash
make local
```

Windows如果没有make可以参考`scripts/local_setup.sh`手动设置

同理， 在 `dongfeng-core-proxy` 根目录下执行

```bash
make local
```

## 启动 Micro API Gateway

```bash
micro api --namespace=dongfeng.svc.core.proxy --handler=proxy
```

## 启动微服务

在 `dongfeng-core/service/server` 下执行

```bash
go run main.go
```

在 `dongfeng-core-proxy/service/server` 下执行

```bash
go run main.go
```

## 访问 `localhost:8080/api`