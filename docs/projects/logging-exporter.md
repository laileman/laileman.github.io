# logging exporter

## 项目简介

Logging Exporter 是一个将日志数据转换为 Prometheus 可识别的 metrics 并进行上报的工具。它支持多种数据存储后端，方便用户通过 Prometheus 监控日志相关指标。

## 主要功能

- 将日志数据转换为 Prometheus metrics
- 支持多种数据存储后端：Elasticsearch、MySQL、stdout-json、InfluxDB
- 提供 HTTP 接口，方便 Prometheus 抓取指标
- 基于 Go 语言开发，使用 Gin 框架构建高性能服务

## 技术栈

- 语言：Go
- 框架：Gin
- 数据库：Elasticsearch、MySQL、InfluxDB、stdout-json

## 使用说明

1. 配置数据源和指标转换规则
2. 启动服务，监听指定端口
3. Prometheus 配置抓取该服务的 metrics 接口

## 架构

[filename](_image/logging-exporter.drawio ':include :type=code')
