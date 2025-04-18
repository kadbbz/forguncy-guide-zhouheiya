# 服务配置

【<font color="#1677FF">推荐</font>】请务必启用 HTTPS。

::: tip 🔔 TIP
- 推荐在 nginx 上配置 SSL 证书，实现 HTTPS 访问。
- 对于不使用 nginx 的小型应用，也可以在活字格服务管理控制台上配置 SSL 证书，在发布应用时勾选「启用 SSL（HTTPS）」。
:::

【<font color="#1677FF">推荐</font>】请为您的应用服务设置合理的跨域访问策略（如 deny）。除非必要，不要将白名单设置为 `*`。

【<font color="#1677FF">推荐</font>】定期重置已发放给第三方的客户端授权的秘钥。

【<font color="#1677FF">推荐</font>】如有需要，请构建全局变量管理平台。

::: info 📍 INFO
目前生产环境下，对全局变量的管理需要进入服务端管理控制台的应用界面进行修改。
而全局变量的使用场景，可能存在频繁变更的情况。 可以考虑使用「设置全局变量命令」构建独立的配置平台，将全局变量的维护与服务端管理控制台解耦。
:::

【<font color="#1677FF">推荐</font>】将用户信息数据库设置到外联库，并建立备份机制。

【<font color="#1677FF">推荐</font>】将文件路径（尤其是用户上传附件）设置到利于统一的文件夹结构，并建立备份机制。


【<font color="#1677FF">推荐</font>】为应用设置合理的日志监控策略。

::: info 📍 INFO
活字格服务器在记录日志时会占用一定的计算资源和磁盘空间，根据实际情况开启或关闭部分日志可以在保障故障调查的基础上，有效降低资源开销。

|  日志类别   | 测试环境/验证环境  | 生产环境（大版本上线后1个月内）  | 生产环境（稳定运行阶段）  |
|:-------:|:----------:|:-----------------:|:-------------:|
|   异常    |     ON     |        ON         |      ON       |
| HTTP请求  |     ON     |                   |               |
| HTTP响应  |     ON     |        ON         |               |
|  发送邮件   |     ON     |        ON         |               |
|   SQL   |     ON     |        ON         |               |
|  服务端命令  |     ON     |        ON         |               |
|  计划任务   |     ON     |                   |               |
|   登录    |     ON     |       视情况*        |               |
|   登出    |     ON     |       视情况*        |     视情况*      |
|  忘记密码   |     ON     |       视情况*        |     视情况*      |
|   结果    |     ON     |                   |     视情况*      |

<font color="gray" size=2> "视情况*" 表示如果您的企业对于用户登录有数据审计要求，可按需开启对应日志。</font>
:::

【<font color="#1677FF">推荐</font>】定期将应用服务器的应用日志文件/审计日志文件转存到本地，释放服务器的空间资源。





