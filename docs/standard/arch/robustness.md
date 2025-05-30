# 可用性

【<font color="#F3AA34">参考</font>】现代的计算机系统有多重可用性保障机制，故障率已经大幅降低。但仍然存在一些风险因素，有可能导致系统停止服务。除了恶意攻击之外，可用性的典型风险列举如下：

| 典型风险                    | 阶段  | 冷备份  | 热备份  | 其他措施                            |
|:------------------------|:---:|:----:|:----:|:--------------------------------|
| 基础软件系统漏洞（含操作系统、中间件、数据库） | 设计  |      |      | 采用成熟的Linux和数据库版本; <br/>定期升级安全补丁 |
| 应用漏洞                    | 开发  |      |      | 做好测试工作; <br/>定期检查日志，及时发现异常      |
| 硬件损坏（含供电和网络）            | 运维  |  ✅   |  ✅   |                                 |
| 运维误操作                   | 运维  |  ✅   |  ✅   |                                 |
| 请求超过系统处理能力              | 运维  |      |  ✅   |                                 |

【<font color="#F3AA34">参考</font>】在运维层面，冷热备份机制能有效防范可用性风险。冷备份重点防范硬件损坏和运维误操作，热备份在冷备份的基础上，还能通过提升系统处理能力，应对“请求超过系统处理能力”的风险。

::: tip 🔔 TIP
在具体操作时，冷备份通常是指参照生产环境的配置，另外搭建一套备份环境。生产环境的应用升级时，手动更新备份环境；数据则通过定时的数据备份/恢复机制实现同步。如果生产环境出现故障，则通过DNS、负载均衡器或前置nGinx等机制，将备份环境切换为生产环境使用。

热备份则推荐可以使用集群部署来代替。
:::