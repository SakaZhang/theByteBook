# 分布式事务

:::tip <a/>

Repair what you can — but when you must fail, fail noisily and as soon as possible.

:::
对于分布式事物的定义，先来看看 WIKI 百科的解释。

:::tip 分布式事务
A distributed transaction is a database transaction in which two or more network hosts are involved.
:::

提及事务，最早是指涉及操作多个资源的数据库事务问题，不过随着 SOA、微服务架构逐渐流行之后，分布式事务的概念也被泛化，事务的处理已经不再局限在数据库范围内，所有需要保证数据一致性的应用场景，包括但不限于缓存、消息队列、分布式存储、多个微服务之下的业务一致性处理等等都需要用到事务进行处理。**如果事务的影响只局限在本地，如何实现事务仅是个编码问题，但如果涉及了多个服务，保证分布式系统下整体的原子性与一致性便成了架构设计问题**。

在 2000 年以前，人们曾经希望 XA 的事务机制在分布式环境下也能良好的应用，但这个愿望被 CAP 定理彻底粉碎，分布式事务的篇章我们就从 ACID 与 CAP 的矛盾说起。