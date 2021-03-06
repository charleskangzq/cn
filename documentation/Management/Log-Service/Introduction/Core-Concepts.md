# 核心概念

**日志主题**  

日志主题是日志采集存储的单位，方便用户将某应用程序所产生的同类型的日志进行统一存储。 

**日志集**

日志集是日志主题管理的单位，用于保存某服务下不同应用程序产生的各类日志主题。  

**采集配置** 

采集配置是指采集日志相关的配置信息，需指定日志来源，当前仅支持选择云产品，需配置所属产品、日志类型及采集的实例对象。  

**全文检索**  

日志中的内容不区分key和value，只要符合检索条件即可。  

**键值检索**  

日志中的内容区分key和value，可以针对特定Key的值进行快速精确的查询。

**日志转储**

将日志数据按照设置的转储规则存储对对象存储OSS中，并且可以在所转储的对象存储bucket中下载日志文件，进行审计、离线分析等。

**日志监控**

针对有监控需求的日志，设置筛选条件，对符合筛选条件的日志数据中的关键词或指定字段设置监控，可以查看监控图，设置报警规则。
