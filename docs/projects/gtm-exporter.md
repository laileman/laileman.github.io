# gtm-exporter

> 目的： 将日志中的gtm信息暴露成metrics, 用于监控gtm的运行状态和进行数据分析

## 架构

[filename](_image/gtm-exporter.drawio ':include :type=code')

## 功能说明

- client: 客户端请求带有客户ip,包大小...等信息
- gtm server: 运行在多个kubernetes集群的pod, 将客户端请求的信息输出到日志的标准输出
- fluent-bit: 运行在kubernetes集群daemonset, 从标准输出中拉取日志, 并从 mpid-server 中获取ip 所对应的 mpid,追加到日志中，把日志输出到 influxdb 进行一步计算
- influxdb: 存储gtm信息的数据库
- data-exporter: 对 influxdb 中的数据进行处理,例如平均值, 中位数,最大值....并将其转暴露为 metrics
- prometheus: 从data-exporter中拉取metrics, 大数据系统也从prometheus api 获取 gtm metrics进行数据分析
- grafana: 可视化展示gtm metrics