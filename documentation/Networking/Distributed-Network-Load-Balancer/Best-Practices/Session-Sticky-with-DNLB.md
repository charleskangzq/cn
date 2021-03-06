# 后端服务器稳定情况下，实现业务会话保持

分布式网络负载均衡仅能为四层无状态业务提供负载均衡服务，不支持会话保持。当后端服务器稳定的情况下，可通过配置按加权源IP进行调度的监听策略，实现相同源IP的业务请求转发到相同的后端服务器，满足业务源IP不变情况下的会话保持需求。

## 准备与规划

- 网络准备

  根据业务部署需要，提前规划分布式网络负载均衡和作为后端服务器的云主机/容器的地域、可用区、私有网络等。

      注意: 作为后端服务器的云主机/容器需与分布式网络负载均衡属于同一地域和私有网络。

- 服务器准备

  需提前创建承载业务流量的云主机/容器，并确保打开监听所需的端口，合理配置安全组和ACL策略。
  
- 负载均衡实例

  创建一个分布式网络负载均衡实例，并设置地域、网络等配置。
## 操作步骤
1.您可以在分布式网络负载均衡列表页通过以下两种方式，进入监听器列表页。

   - 点击 **名称**  栏下的指定分布式网络负载均衡，进入该分布式网络负载均衡详情页。点击 **监听器** 页签，进入监听器列表页。
   - 点击 **操作** 栏下的 **添加监听** 链接，进入监听器列表页。

2.点击 **新建监听器** 按钮，在弹出的配置向导对话框中配置监听协议和端口。

3.点击 **下一步** 进入后端转发配置页签。选择默认后端服务类型：

   - 如分布式网络负载均衡下没有后端服务或现有后端服务不能满足业务需求，请选择 **新建后端服务**。
   - 如分布式网络负载均衡下已有后端服务满足业务需求，可选择 **选择后端服务**，新建监听器将与其他监听器共用选择的后端服务。

4.本举例中选择新建后端服务，配置后端服务名称和后端协议，调度算法选择 **加权源IP**。

5.点击 **下一步** 进入健康检查配置页签。本举例中健康检查参数都使用默认，用户可根据需求修改。

6.点击 **下一步** 进入添加服务器组页签。添加虚拟服务器或高可用组作为后端服务器。

7.点击 **确定** 按钮，完成创建监听器的操作。



