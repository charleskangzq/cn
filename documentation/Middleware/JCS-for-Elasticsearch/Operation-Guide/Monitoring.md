## 查看监控信息
集群创建成功后，单击集群名称进入集群详情页，可以查看关于集群运行的详细监控信息，辅助集群运维监管。也可由“云监控-资源监控-Elasticsearch监控”进入查看。</br>
### 操作步骤
1.访问[云搜索Elasticsearch控制台](https://es-console.jdcloud.com/clusters)，即进入集群列表页面。</br>

2.在集群列表页面，点击集群名称，进入详情页面。</br>

3.在详情页面，点击【集群监控】进入监控页面。</br>

4.监控时段可选择据当前时间“1小时”、“6小时”、“12小时”进行选择，也可由日历时间段自主选择。</br>

5.单击右上方“设置报警规则”，单击跳转至云监控页面进行报警规则的设置。</br>

![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/监控ES.png)
 
监控指标包括：集群健康状态、集群查询QPS、集群写入QPS、节点CPU使用率、节点磁盘使用率、节点HeapMemory使用率。</br>

| 监控项	| 说明	|
|:--:|:--:|
| 集群状态 | 0 表示绿色，此时集群处于最健康状态；1 表示黄色，此时集群的高可用性受到影响，但是搜索结果仍然完整；2 表示红色，此时集群异常，搜索只能返回部分数据 |
| 集群查询QPS（Count/Second） 	| 反应集群查询操作繁忙程度 |
| 集群写入QPS（Count/Second） | 反应集群写入操作繁忙程度 |
| CPU节点利用率（%） | CPU 使用率过高会导致集群节点处理能力下降，甚至宕机 |
| 节点磁盘使用率（%） 	| 磁盘使用率过高会导致数据无法正常写入 |
| 节点HeapMemory使用率（%） |数值过高时影响查询性能 | 

其中健康状态是云搜索Elasticsearch集群非常重要的监控项，用来表征集群总体上是否工作正常。健康状态种类如下：</br>

|颜色 | 健康状态	|
|:--:|:--: |
| 绿色（green） | 所有的主分片和副本分片都已分配，集群是100%可用的。	|
| 黄色（yellow） | 所有的主分片已经分片了，但至少还有一个副本是缺失的。高可用性在某种程度上被弱化。	|
| 红色（red） | 至少有一个主分片（以及它的全部副本）都在缺失中。 |
