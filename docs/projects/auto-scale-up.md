# kubernetes auto scale up

> ref: https://www.spectrocloud.com/blog/kubernetes-autoscaling-patterns-hpa-vpa-and-keda

# 目前流程

- 每周活动，网络流量突增 --> 添加副本， 活动结束，网络流量降低， 减少副本

- redis集群：  负载高--> 升级
