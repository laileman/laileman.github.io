# 项目说明

- [配置中心](配置中心.md):
    - 统一管理各个服务的配置,提供配置管理、版本管理、灰度发布、权限管理等功能


- [Lark-alert](lart-alert.md): 
    - alertmanager 原生不支持直接发送告警到飞书，此组件是接收alertmanager webhook,转发到飞书群组，支持@值班人员。 同时支持 pagerduty格式的告警。
    - language: go
    - framework: gin

- [Logging-exporter](logging-exporter.md): 
    - 日志转换成 metrics, 并上报到 prometheus。
    - language: go
    - framework: gin
    - db: elasticsearch, mysql, stdout-json, influxdb
    - language: go

- [Metedata-database](metadata-database.md): 
    - 元数据数据库，存储集群、网络，存储，地区，机房等信息。提供 api 接口，方便其他组件调用。例如 sli, 自动部署集群。和将新集群信息插入到 metedata-database。
    - db: mysql
    - language: python
    - framework: fastapi

- [sil-exporter](sli-exporter): 
    - 从metadatabase中获取sil数据，并将暴露给prometheus 收集
    - language: go
    - framework: gin
    - db: mysql,postgres
