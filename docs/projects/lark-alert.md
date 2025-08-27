# lart-alert

## 功能
> 基于飞书机器人的报警功能

1. alertmanager 发送告警到 pagerduty，pagerduty将报警转发的飞书
2. 飞书连接oncall platform, 获取指标人员信息
3. 支持在飞书上acknowledge，resolve添加评论到 pagerduty告警

## 拓扑

[filename](_image/lark-alert.drawio ':include :type=code')