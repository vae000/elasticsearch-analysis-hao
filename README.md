# 源自
- fork 自 hao 分词器，8.7.1 (https://github.com/tenlee2012/elasticsearch-analysis-hao)

# 修改记录
## 2025.8 解决高版本（ES 8.19）编译及权限问题
### 问题一：Inject 依赖注入
- Elasticsearch 8.19 的 SDK 不再有 org.elasticsearch.common.inject.Inject 包，移除替换之
### 问题二：远程词典获取问题
- Elasticsearch 8.19 的插件网络权限不再由 plugin-security.policy 控制，改为由 entitlement-policy.yaml 控制，需要替换，可以参考官方文档：Creating classic plugins
```
ALL-UNNAMED:
- manage_threads
- outbound_network
```

## 2025.11 细颗粒度模式分词结果调整
- 原分词器，`体力值`，分词结果只存`体力值`,`体力`,而不存`值`
- 修改后，如果 `值` 在词典中，分词结果为 `体力值`、`体力`、`值`
