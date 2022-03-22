# ClickHouse-operator
# 0.镜像制作
```shell
docker pull yandex/clickhouse-server
```

# 1.启动clickhouse-operator

If you want to install operator on kubernetes version prior 1.17 in kube-system namespace
just run:
```shell
kubectl apply -f https://raw.githubusercontent.com/Altinity/clickhouse-operator/master/deploy/operator/clickhouse-operator-install-bundle-v1beta1.yaml
```

新版的话直接使用最新的脚本
https://github.com/Altinity/clickhouse-operator/blob/master/docs/quick_start.md

# 2.启动zookeeper
目前使用helm
注意head内存，不能过小，否则会选举失败
```shell
helm install ./zookeeper --namespace ch-operator --generate-name
```

# 3.启动clickhouse
```shell
kubectl create ns ch-operator
```

**注意：**修改zookeeper.nodes.host去连接指定的zk
```shell
kubectl apply -f ./pod.yaml -n ch-operator
```


