# sli-exporter

> exporter for SLI metrics

## 功能

- 支持将 SLI 指标导入到 Prometheus 中
- 支持从数据库 mysql,postgresql 等导入 SLI 指标
- 提供高效稳定的指标采集服务，适合大规模生产环境

## 项目简介

SLI Exporter 是一个专门用于导出服务级别指标（SLI）的 Prometheus Exporter。它能够从多种数据库中获取 SLI 数据，并将其转换为 Prometheus 可采集的指标，方便监控和告警。

## 主要功能

- 支持将 SLI 指标导入到 Prometheus 中进行监控
- 支持从 MySQL、PostgreSQL 等数据库导入 SLI 指标数据
- 提供高效稳定的指标采集服务，适合大规模生产环境

## 技术栈

- 语言：Go
- 框架：Gin
- 数据库支持：MySQL、PostgreSQL

## 使用说明

1. 配置数据库连接信息和查询语句
2. 启动 SLI Exporter 服务
3. 配置 Prometheus 抓取 SLI Exporter 暴露的指标接口

## 架构

[filename](_image/sli-exporter.drawio ':include :type=code')
