# Unified Messaging Center

## 目前拓扑

[old](_image/umc-old.drawio ':include :type=code')

缺点

- SRE 和 DBA 运维重复相同的报警线路，
- 开发生产环境单独部署相同的相同的功能
- 升级/变更 需要涉及多套环境，重复操作成本过高
- SRE/DBA 割裂成两个不同小组
- 报警到飞书多群组，不利于检查报警
- alertmanager 不具备收敛功能，会导致飞书群组刷屏
- SNS/lamdba 功能重复，造成重复成本

## 新拓扑

[new](_image/umc-new.drawio ':include :type=code')

优点

- 只需要维护一个lamdba 函数, 实现所有功能，减少重复运维成本
- 将报警存储到数据库进行筛选分析比较，重复的报警进行受理避免飞书刷屏
- 支持自动化运维脚本的消息,自动化任务执行情况，通过飞书查看
- 支持发送 SMS
- 一个 SNS满足所有的AWS报警,减少AWS的重复成本

开发语言：

golang, postgres