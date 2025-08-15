# gtm-exporter
> 目的： 将日志中的gtm信息暴露成metrics, 用于监控gtm的运行状态和进行数据分析

## 架构
[filename](_image/gtm-exporter.drawio ':include :type=code')

## 功能说明
- client: 客户端请求带有客户ip,包大小...
- gtm pod: 运行在gtm节点的pod, 将客户端请求的信息输出到日志的标准输出
- fluent-bit: 运行在gtm节点的pod, 从标准输出中拉取日志, 并从 redis 中获取ip 所对应的 mpid,最佳到日志中，并将日志中的gtm信息输入到influxdb
- influxdb: 存储gtm信息的数据库
- data-exporter: 对 influxdb 中的数据进行处理,例如avg,sum,max,min, 并将其转换为 metrics
- prometheus: 从data-exporter中拉取metrics, 并将其转换为metrics
- grafana: 可视化展示gtm metrics

## 代码仓库
https://github.com/laileman/gtm-exporter
- gtm-pod: 模拟生产环境的gtm pod,将一些客户端的信息输出到标准输出日志
- data-exporter: 从influxdb中拉取数据, 并将其转换为metrics
- mpid-server: 负责存储mpid信息, 存储数据在redis，并提供api接口

## 部署
```bash
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/gtm-pod
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/fluent-bit
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/mpid
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/influxdb
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/data-exporter
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/prometheus
kubectl apply -f https://raw.githubusercontent.com/laileman/gtm-exporter/main/deploy/grafana

```

## 模拟数据
- 插入mpid
```bash
curl -X POST http://localhost:8080/mpid -d '{"ip": "10.0.0.1", "mpid": "123456"}'
```
- 插入gtm信息
```bash
curl -X POST http://localhost:8080/gtm -d '{"ip": "10.0.0.1", "mpid": "123456", "client": "10.0.0.2", "size": 1000000, "time": 1000000000000000000}'
```

## 可视化
访问 http://localhost:3000