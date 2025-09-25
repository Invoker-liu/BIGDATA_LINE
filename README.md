# BigData_Line

* 《hadoop权威指南》：https://download.csdn.net/download/singgel/10863323

* 《Flume日志收集与MapReduce模式》https://download.csdn.net/download/singgel/10958726

## HIVE HBASE FLINK KYLIN

[万亿数据下的多维实时分析系统，如何做到亚秒级响应](https://mp.weixin.qq.com/s/D1Ta8lZI7bDRhLTFbEuohw)  

[高效大数据开发之 bitmap 思想的应用](https://mp.weixin.qq.com/s/c5HDenoVde11IMmezj1v1Q)  

[滴滴实时数仓逐层剖解：实时与离线数据误差<0.5%](https://mp.weixin.qq.com/s/xEUL5ust9btXqiNiMm5wPQ)  

[数仓引入ClickHouse之后，性能提升了400%！](https://mp.weixin.qq.com/s/mJplgZmU6OZqE30cfJvw7Q)  

[pache Kylin的实践与优化](https://mp.weixin.qq.com/s/0S1ih4SJ7xEu0h557yJmgA)  
* 美团之前没有好好的看kylin的源码和配置参数，导致线上的CPU、内存、文件数没有规划  
* 引擎升级至：spark（最近是flink了） 数据源采用hive 全局字典依赖配置  

[应对万亿数据上亿并发！字节跳动的图数据库研发实践](https://mp.weixin.qq.com/s/WyOMumZyqs_ouaPJpJouNg)  
* 自研的图数据库：解决了热点无问题，性能单节点R:200k W:10k  
* 不支持ACID事务、总之还在发展中  

[基于Kafka+Flink平台化设计，实时数仓还能这样建](https://mp.weixin.qq.com/s/0wF_C8mpYBb8KFB0KhwodA)  
* 网易云音乐将实时计算的多个sink下kafkasource的重复消费问题：增加了一个data update标记同一个表计算合并  
* 多个kafka集群部署在一个交换机下，离线计算和实时计算等其他情况造成的交换机带宽问题：拆分机房规划  

[HBase数据迁移到Kafka？这种逆向操作你懵逼了吗？](https://mp.weixin.qq.com/s/-J9nQs8IjEOcSj849tYigg)  

[知乎 HBase 实践](https://mp.weixin.qq.com/s/U1zCtD0fJIBJR2PNA_3JQA)  

[两小时搞定PB级HDFS数据迁移，挪走日均近5亿RPC](https://mp.weixin.qq.com/s/DZQO7TCdUOsh4ETza3epVg)  

## REDIS ES MYSQL MongoDB

[Redis 进阶笔记](https://mp.weixin.qq.com/s/o66KCbJUj4RsgXFjXzLzoQ)  
1.Redis 里的 List 设计非常牛，当数据量比较小的时候，数据结构是压缩链表，而当数据量比较多的时候就成为了快速链表。  
2.hash 的扩容 rehash 过程就是维护了两个 hash 结构，如果需要扩容的时候，就把新的数据写入新字典中，然后后端起一个线程来逐步迁移，总体上来说就是采用了空间换时间的思想。  
3.对于上游的客户端请求，采用了多路复用的原理。Redis 会给每一个客户端套接字都关联一个指令队列，客户端的指令队列通过队列排队来进行顺序处理，同时 Reids 给每一个客户端的套件字关联一个响应队列，Redis 服务器通过响应队列来将指令的接口返回给客户端  
在 Redis 4.0 之后，支持了混合持久化 RDB + 增量的 AOF 文件  

[这篇Redis文章，Antirez看了都说好](https://mp.weixin.qq.com/s/DCngASQ7gsKpFA2JHCH7Sg)  
mem_fragmentation_ratio一般大于1，且该值越大，内存碎片比例越大。如果mem_fragmentation_ratio<1，说明Redis使用了虚拟内存，由于虚拟内存的媒介是磁盘，比内存速度要慢很多，当这种情况出现时，应该及时排查，如果内存不足应该及时处理  

[聊一聊Redis持久化开与关](https://mp.weixin.qq.com/s/TZnDk_5qScLFPGPhwrxTQA)  
**RDB备份**格式多变（Redis 3 4 5 6版本多次修改）  
**AOF备份**加载慢：利用fakeclient做回放，AOF重写还是动作不，开启AOF后，Redis的写性能下降了8~25%，读性能未下降  
**RDB-AOF混合**持久化文件全量使用RDB，增量使用AOF，保证体积、实时性、加载速度。  

[Redis小功能大用处(1)  -stat_expired_time_cap_reached_count](https://mp.weixin.qq.com/s/3UxXnSus0HTlA0ndpLZPgg)  

[Redis常见客户端异常汇总(Jedis篇)  ](https://mp.weixin.qq.com/s/T-BBlAQ4B5qj0VCTKUMgXA)  

[Redis在Linux系统的配置优化](https://mp.weixin.qq.com/s/eN8qQn9HjeI1BV-MMFcWiw)  

[Redis module功能介绍](https://mp.weixin.qq.com/s/uN1Iyha96TCG7Ff2ZRW1Dw)  

[Redis 6.2 RC发布新特性一览](https://mp.weixin.qq.com/s/dwUze7I2zoryNmTHmrG5PQ)  

[败家玩意儿！Redis 竟然浪费了这么多内存！](https://mp.weixin.qq.com/s/efPjJjdDHW6QOhSfHOioRA)  

[从1到3分布式Redis电商实战&缓存穿透&缓存雪崩&缓存失效终极解决](https://www.bilibili.com/video/BV17T4y1F79p?p=1&share_medium=android&share_plat=android&share_source=COPY&share_tag=s_i&timestamp=1607301887&unique_k=sVref8)  

[替你踩过Redis缓存的坑，奉上使用规范和监控方法](https://mp.weixin.qq.com/s/R-slZDV2YNTA_M_sctyvZA)  

[Redis为什么变慢了？Redis性能问题排查详述](https://mp.weixin.qq.com/s/gYQn9tdFK9tHJDoMWcU4cQ)  
超级实用，建议看原文  

[运维：终于不用再背着数万实例的Redis集群了](https://mp.weixin.qq.com/s/F5Wn6OWKzswA4tg2fHrevw)  

[一万字详解 Redis Cluster Gossip 协议](https://segmentfault.com/a/1190000038400015)  

[Codis VS Redis Cluster：我该选择哪一个集群方案](https://time.geekbang.org/column/article/85495ce4171a7dc638c424414e229cac/share)  
codis提供了  
1.dashboard的fe界面运维简单  
2.基于zookeeper的proxy代理slot-mapping映射  
3.基于sentinel的主从切换高可用  
codis提供了异步的数据迁移方案（其中对大key拆分迁移的原子性方案），对比redis-cluster来说相对应用较早  

[Redis 缓存性能实践及总结](https://mp.weixin.qq.com/s/bsAw0VKhP_SYngvKMoByAQ)  

[Redis小功能大用处-total_net_output_bytes](https://mp.weixin.qq.com/s/emr4_clKV4qW0gmtHiINiQ)  

[Redis速度快的原因：几点图解总结](https://mp.weixin.qq.com/s/FtfAqXXDef6-bhuGyPDK7w)  

[深入浅出百亿请求高可用Redis(codis)  分布式集群揭秘](https://mp.weixin.qq.com/s/F68-e2umTQIq0aGfif58ow)  

[干货 | 数万实例数百TB数据量，携程Redis治理演进之路](https://mp.weixin.qq.com/s/L7EQzthCoWuJw8TzY-KAMw)  

[干货 | 携程Redis治理演进之路（二）](https://mp.weixin.qq.com/s/QTqcBZlAhp5cLRJGJVZRNw)  

[pika集群水平扩展——让性能容量不再受限](https://mp.weixin.qq.com/s/xksAosZSpLVjb1JuX5XhRQ)  

[Spark-Redis入门到解决执行海量数据插入、查询作业时碰到的问题](https://mp.weixin.qq.com/s/K84I-mUf7U9Iej6h3un-bQ)  

[超全的数据库建表/SQL/索引规范，适合贴在工位上！](https://mp.weixin.qq.com/s/-_m-OJ_PUXrw8Gey2ZA9aA)  

[MySQL 5.6.35 索引优化导致的死锁案例解析](https://mp.weixin.qq.com/s/T5e-gb0MXxjBwbjGg6jIMg)  
原因是:index_merge是MySQL 5.1后引入的一项索引合并优化技术，它允许对同一个表同时使用多个索引进行查询，并对多个索引的查询结果进行合并(取交集(intersect)  、并集(union)  等)  后返回。  
死锁的本质原因还是由加锁顺序不同所导致，是由于Index Merge同时使用2个索引方向加锁所导致，解决方法也比较简单，就是消除因index merge带来的多个索引同时执行的情况。  

[让MySQL飞起来！别小看这21种写SQL的好习惯](https://mp.weixin.qq.com/s/snV9i2qUR1yUje80YzxwOg)  
* 操作delete或者update语句，加个limit  
* SQL命令行修改数据，养成begin + commit 事务的习惯  
* 写完SQL先explain查看执行计划  
* 如果修改/更新数据过多，考虑批量进行  

[我在MySQL原厂的那些年都经历了什么？](https://mp.weixin.qq.com/s/HW7tji_fQBeOa7kr2xsmtg)  

[高并发场景下，百万级订单量系统的分库分表重构经历](https://mp.weixin.qq.com/s/Mp6yyS3VVj2v1D1gxuojwA)  

[3年部署3000套PG实例的架构设计与踩坑经验](https://mp.weixin.qq.com/s/OPQr248yiwFI9Q6vLx9tZw)  

[简述3种CQRS架构模式](https://mp.weixin.qq.com/s/pToMvg5tNJKfRmJdNfXicw)  

[InnoDB 事务加锁分析](https://mp.weixin.qq.com/s/S7MhlsZveBHRSQhq5aTIJA)  

[MySQL 的 crash-safe 原理解析](https://mp.weixin.qq.com/s/5i9wmJs4_Er7RaYfNnETyA)  

[MySQL 8 新特性之Clone Plugin](https://mp.weixin.qq.com/s/_HqRXhQX_6e0boACzcAH8g)  

[MySQL 索引知识点总结](https://mp.weixin.qq.com/s/QduIxKOykMmoZp13UGF1XQ)  

[API 分页设计与实现](https://mp.weixin.qq.com/s/TQ248e9171jOHSYxdgLBWA)  
在数据库中有一个游标（cursor）的概念，它是一个指向行的指针，然后可以告诉数据库："在这个游标之后返回 100 行"。  
使用游标的另一个原因是避免由于并发编辑而导致元素重复或跳过的问题,而不用担心新的记录进来扰乱你的分页。  

[一次看完28个关于ES的性能调优技巧](https://mp.weixin.qq.com/s/nnOazH26pq-Kn8zlGKgvTA)  

[ElasticSearch使用规范beta版](https://mp.weixin.qq.com/s/yCTNH1hMp6iOvHgh9vWg6A)  
* 非日志型(搜索型、线上业务型)  的shard容量在10~30GB（建议在10G）  
* 日志型的shard容量在30~100GB（建议30G）  
* 单个shard的文档个数不能超过21亿左右(Integer.MAX_VALUE - 128)  
* 一个节点管理的shard数不要超过200个  
* routing id不均衡：集群容量和访问不均衡，对于分布式存储是致命的  
* 拒绝大聚合 ：ES计算都在JVM内存中完成  
* 拒绝模糊查询：es一大杀手  
* 拒绝深度分页  
* 禁止查询 indexName-*  

[Elasticsearch分布式一致性原理剖析(一)-节点篇](https://zhuanlan.zhihu.com/p/34830403)  
1 扩容DataNode  
2 缩容DataNode 我们需要把这个Node上的Shards迁移到其他节点上，方法是先设置allocation规则，禁止分配Shard到要缩容的机器上，然后让集群进行rebalance。  
3 扩容MasterNode 假设之前3个master-eligible node，我们可以配置quorum为2，如果扩容到4个master-eligible node，那么quorum就要提高到3。  
4 缩容MasterNode  
ES的leader选举：  
**是否有选举周期term**：raft引入了选举周期的概念，每轮选举term加1，保证了在同一个term下每个参与人只能投1票。ES在选举时没有term的概念，不能保证每轮每个节点只投一票。  
**选举的倾向性**：raft中只要一个节点拥有最新的已提交的数据，则有机会选举成为master。在ES中，version相同时会按照NodeId排序，总是NodeId小的人优先级高。 

[Elasticsearch分布式一致性原理剖析(二)-Meta篇](https://zhuanlan.zhihu.com/p/35283785)  
MetaData是由Master管理的，为什么DataNode上也要保存MetaData呢？主要原因是考虑到数据的安全性，很多用户没有考虑Master节点的高可用和数据高可靠，在部署ES集群时只配置了一个MasterNode，如果这个节点不可用，就会出现Meta丢失，后果非常严重。  

[Elasticsearch分布式一致性原理剖析(三)-Data篇](https://zhuanlan.zhihu.com/p/35285514)  
* ES写入流程为先写入Primary，再并发写入Replica，最后应答客户端  
**waitforactiveshards** 这个参数默认是1，即只要Primary在就可以写入，起不到什么作用。如果配置大于1，可以起到一种保护的作用，保证写入的数据具有更高的可靠性。  
**为何要等待所有Replica响应(或连接失败)后返回?**  
在更早的ES版本，Primary和Replica之间是允许异步复制的，即写入Primary成功即可返回。  
如果Replica写入失败，ES会执行一些重试逻辑等，但最终并不强求一定要在多少个节点写入成功。在返回的结果中，会包含数据在多少个shard中写入成功了，多少个失败了  
**如果某个Replica持续写失败，用户是否会经常查到旧数据？**  
如果一个Replica写失败了，Primary会将这个信息报告给Master，然后Master会在Meta中更新这个Index的InSyncAllocations配置，将这个Replica从中移除，移除后它就不再承担读请求。  
**为什么要写translog？**  
1. translog类似于数据库中的commitlog，或者binlog。只要translog写入成功并flush，那么这笔数据就落盘了，数据安全性有了保证，Segment就可以晚一点落盘。  
2. translog记录了每一笔数据更改，以及数据更改的顺序，所以translog也可以用于数据恢复。  
3. 用于Primary和新的Replica之间的数据同步，即Replica逐步追上Primary数据的过程。  
**PacificA算法** 是微软亚洲研究院提出的一种用于日志复制系统的分布式一致性算法  
Reconfiguration：Secondary故障，Primary故障，新加节点  
SequenceNumber、Checkpoint与故障恢复  
LocalCheckpoint和GlobalCheckpoint  

[Elasticsearch内核解析 - 写入篇](https://zhuanlan.zhihu.com/p/34669354)  
* ES的写操作是primary写入完成之后，同时给replica
源码位置：org.elasticsearch.action.support.replication.ReplicationOperation#execute
写入操作的延时 latency = Latency(Primary Write) + Max(Replicas Write)  
![20210823161847.jpg](pic/20210823161847.jpg)  
**可靠性**：由于Lucene的设计中不考虑可靠性，在Elasticsearch中通过Replica和TransLog两套机制保证数据的可靠性。  
**原子性**：Add和Delete都是直接调用Lucene的接口，是原子的。当部分更新时，使用`Version`和锁保证更新是原子的  
**性能**  
一是不需要所有Replica都返回后才能返回给用户，只需要返回特定数目的就行；  
二是生成的Segment现在内存中提供服务，等一段时间后才刷新到磁盘，Segment在内存这段时间的可靠性由TransLog保证；  
三是TransLog可以配置为周期性的Flush，但这个会给可靠性带来伤害；  
四是每个线程持有一个Segment，多线程时相互不影响，相互独立，性能更好；  
五是系统的写入流程对版本依赖较重，读取频率较高，因此采用了versionMap，减少热点数据的多次磁盘IO开销。  

[Elasticsearch调优实践](https://mp.weixin.qq.com/s/0TMESj2Z-XK2PzwBQo0Mpg)  
```
一 Linux参数调优
mount -o noatime,data=writeback,barrier=0,nobh /dev/sda /es_data

二 ES 节点配置
1. 适当增大写入 buffer 和 bulk 队列长度，提高写入性能和稳定性
2. 计算 disk 使用量时，不考虑正在搬迁的 shard
cluster.routing.allocation.disk.include_relocations: false

三 ES 使用方式
1. 控制字段的存储选项 
    StoreFiled： 行存，其中占比最大的是 source 字段，它控制 doc 原始数据的存储。
    注意：关闭 source 后， update, updatebyquery, reindex 等接口将无法正常使用，所以有 update 等需求的 index 不能关闭 source。
    docvalues：控制列存. ES 主要使用列存来支持 sorting, aggregations 和 scripts 功能，对于没有上述需求的字段，可以关闭 docvalues，降低存储成本。
    index：控制倒排索引。ES 默认对于所有字段都开启了倒排索引，用于查询。对于没有查询需求的字段，可以关闭倒排索引。
    all(6.0+版本已删除)：ES 的一个特殊的字段，ES 把用户写入 json 的所有字段值拼接成一个字符串后，做分词，然后保存倒排索引，用于支持整个 json 的全文检索。
    fieldnames：该字段用于 exists 查询，来确认某个 doc 里面有无一个字段存在。若没有这种需求，可以将其关闭。
2. 开启最佳压缩
3. bulk 批量写入
    每个 bulk 请求的 doc 数量设定区间推荐为 1k~1w
4. 调整 translog 同步策略
    "sync_interval": "60s"
    "durability": "async"
5. 调整 refresh_interval
    ES 必须通过 refresh 的过程把内存中的数据转换成 Lucene 的完整 segment 后，才可以被搜索。
6. merge 并发控制
    "index.merge.scheduler.max_thread_count": 2
7. 写入数据不指定_id，让 ES 自动产生
    无 id 的数据写入性能可能比有_id 的高出近一倍
8. 使用 routing
    启 routing 功能后，ES 会将 routing 相同的数据写入到同一个分片中（也可以是多个，由 index.routingpartitionsize 参数控制）。
9. 为 string 类型的字段选取合适的存储方式
    string 字段默认类型为 text
    存为 keyword 类型的字段： 不做分词，不支持全文检索。
10. 查询时，使用 query-bool-filter 组合取代普通 query
    通过 query-bool-filter 组合来让 ES 不计算 score，并且尽可能的缓存 filter 的结果集，供后续包含相同 filter 的查询使用，提高查询效率。
11.index 按日期滚动，便于管理
    好处是各种数据分开管理不会混淆，也易于提高查询效率。数据过期时删除整个 index，要比一条条删除数据或 deletebyquery 效率高很多
12. 按需控制 index 的分片数和副本数
    shard 数量过多，则批量写入 / 查询请求被分割为过多的子写入 / 查询，导致该 index 的写入、查询拒绝率上升；
    对于数据量较大的 index，当其 shard 数量过小时，无法充分利用节点资源，造成机器资源利用率不高 或 不均衡，影响写入 / 查询的效率。
    对于数据较大的index：
        可通过 index.routing.allocation.totalshardsper_node 参数，强制限定一个节点上该 index 的 shard 数量，让 shard 尽量分配到不同节点上
    综合考虑整个 index 的 shard 数量，如果 shard 数量（不包括副本）超过 50 个，就很可能引发拒绝率上升的问题，
    此时可考虑把该 index 拆分为多个独立的 index，分摊数据量，同时配合 routing 使用，降低每个查询需要访问的 shard 数量。

1. 节点数较多的集群，增加专有 master，提升集群稳定性
    ES 集群的元信息管理、index 的增删操作、节点的加入剔除等集群管理的任务都是由 master 节点来负责的，master 节点定期将最新的集群状态广播至各个节点。
    master 节点，这些节点只负责集群管理，不存储数据，不承担数据读写压力；其他节点则仅负责数据读写，不负责集群管理的工作。
2. 控制 index、shard 总数量
    基础架构部数据库团队曾经在一个 20 个节点的集群里，创建了 4w + 个 shard，导致新建一个 index 需要 60s + 才能完成。
3. Segment Memory 优化
    当集群的数据量过大时，SegmentMemory 会吃掉大量的堆内存，而 JVM 内存空间又有限，此时就需要想办法降低 SegmentMemory 的使用量了，常用方法有下面几个
        定期删除不使用的 index
        对于不常访问的 index，可以通过 close 接口将其关闭，用到时再打开
        通过 force_merge 接口强制合并 segment，降低 segment 数量
```
[ES集群如何进行挨个重启?](https://elasticsearch.cn/question/4454)

[禁用分片分配的问题](https://elasticsearch.cn/question/4407)  
cluster.routing.allocation.enable: "none"，实际上影响的是已有索引(local存在)  的replica，以及新创建索引的primary和replica。  

[亿级日增量的ES线上环境集群部署，上干货！](https://mp.weixin.qq.com/s/8PjfMqZGDkOk_hv4iIaqNg)  
![20210823153339.jpg](pic/20210823153339.jpg)  
**内存：** 官方标准建议是：将 50％ 的可用内存（不超过 32 GB，一般建议最大设置为：31 GB）分配给 Elasticsearch 堆，而其余 50％ 留给 Lucene 缓存。  
**线程：** 由于 Elasticsearch会做动态分配，除非有非常具体的要求，否则不建议更改线程池和队列大小。  
**分片数：** 建议：为主节点（Master 节点）分配足够的资源以应对分片数过多可能导致的问题。官方给出的合理的建议：每个分片数据大小：30GB-50GB。  
**副本：** 副本越多，数据的容灾性越高。副本多的另一个优点是，每个节点都拥有一个副本分片，有助于提升查询性能。  
**冷热集群架构配置：** 冷热集群架构对于存储诸如应用程序日志或互联网实时采集数据（基于时间序列数据）特别有用。建议：至少运行 3 个热节点以实现高可用性。  
**性能测试工具：** CPU 和 内存的分配最终需要你通过使用与生产环境中类似的环境借助 esrally 性能测试工具测试确定，而不是直接参考各种最佳实践拍脑袋而定。  
![20210823160238.jpg](pic/20210823160238.jpg)  
**节点角色划分**  
1、主节点 如果主节点是仅是候选主节点，不含数据节点角色，则它配置要求没有那么高，因为它不存储任何索引数据。如果分片非常多，建议主节点要提高硬件配置。  
2、数据节点 CURD、搜索以及聚合相关的操作。这些操作一般都是IO、内存、CPU 密集型。  
3、协调节点 类似负载平衡器，主要工作是：将搜索任务分发到相关的数据节点，并收集所有结果，然后再将它们汇总并返回给客户端应用程序。  
**故障排除提示**  
1、堆内存使用率高 在启用垃圾收集时，这些 CPU 周期不可用于处理用户请求。结果，随着系统变得越来越受资源约束，用户请求的响应时间增加。  
2、非堆内存使用率增长 JVM 外非堆内存的增长，吞噬了用于页面缓存的内存，并可能导致内核级OOM。  
3、监控磁盘IO 由于Elasticsearch大量使用存储设备，磁盘 IO 的监视是所有其他优化的基础，发现磁盘 IO 问题并对相关业务操作做调整可以避免潜在的问题  
4、合理设置预警  
5、合理配置缓存 建议在查询中使用 filter 过滤器。  
6、合理设置刷新频率 刷新频率（refresh_interval）和段合并频率与索引性能密切相关，此外，它们还会影响整个集群的性能。  
7、启动慢查询日志 启用慢查询日志记录将有助于识别哪些查询慢，以及可以采取哪些措施来改进它们，这对于通配符查询特别有用。  
8、增大ulimit大小  
9、合理设置交互内存  
10、禁用通配符模糊匹配删除索引 为确保某人不会对所有索引（* 或 _all）发出 DELETE 操作，设置如下："action.destructive_requires_name": true  

[分布式搜索引擎Elasticsearch的架构分析](https://mp.weixin.qq.com/s/N_y7BxbO9pCTrgJbDq4bOA)  

[连环触发！MongoDB核心集群雪崩故障背后竟是……](https://mp.weixin.qq.com/s/3bzKacpe3TD6k0y4pFXHCQ)  

## KAFKA MQ ZOOKEEPER CONSUL

[运维必备：Zookeeper集群“脑裂”问题处理大全](https://mp.weixin.qq.com/s/1NN62CWrCCRpCMNtKsRMvA)  

[深入浅出 ZooKeeper](https://mp.weixin.qq.com/s/umJXy8SXG9r5wYFPPle_WA)  

[基于Consul服务注册中心：一次故障分析及优化](https://mp.weixin.qq.com/s/j1F6KU-q3B890S5tEbTH5A)  
1. 首先网络抖动，导致大量PreparedQuery请求积压在Server中，同时也造成了大量的goroutine和内存使用  
2. 在网络恢复之后，积压的PreparedQuery继续执行，这些goroutine在执行时都会更新metrics从而去获取全局的sync.Mutex，此时切换到starvation模式并且性能下降，大量时间都在等待sync.Mutex，请求阻塞超时；除了积压的goroutine，新的PreparedQuery还在不停接收，获取锁时同样被阻塞，结果是sync.Mutex保持在starvation模式无法自动恢复；  
3. 另一方面raft代码运行会依赖定时器、超时、节点间消息的及时传递与处理，并且这些超时通常是秒、毫秒级别的，但metrics代码阻塞过久，直接导致时序相关的逻辑无法正常运行。

[这样做RabbitMQ高可用，业务流量猛增10倍也不怂](https://mp.weixin.qq.com/s/vLTi_VRjeuW_ekDKzcE5ug)  

[vivo 基于原生 RabbitMQ 的高可用架构实践](https://mp.weixin.qq.com/s/7s9-RsLWgiVvw28U51J0bA)  

[简单理解 Kafka 的消息可靠性策略](https://mp.weixin.qq.com/s/T6gCc8OBgyV-yeAg_MUzPQ)  
**ISR :** leader 副本保持一定同步的 follower 副本, 包括 leader 副本自己，叫 In Sync Replica  
HW: Highwater, 俗称高水位，它表示了一个特定的消息偏移量(offset)  在一个 parttion 中 consumer 只能拉取这个 offset 之前的消息(此 offset 跟 consumer offset 不是一个概念)  
**LEO:** LogEndOffset, 日志末端偏移量, 用来表示当前日志文件中下一条写入消息的 offset  
**leader HW:** 该 Partititon 所有副本的 LEO 最小值  
**follower HW:** min(follower 自身 LEO 和 leader HW)  
**Leader HW** = 所有副本 LEO 最小值  
**Follower HW** = min(follower 自身 LEO 和 leader HW)  
**Leader** 不仅保存了自己的 HW &LEO 还保存了远端副本的 HW &LEO  
在kafka配置为AP系统的情况下发生截断发生的概率会大大提升  
**Kafka Broker** 会在内存中为每个分区都缓存 Leader Epoch 数据，同时它还会定期地将这些信息持久化到一个 checkpoint 文件中  

[从演进式角度看消息队列](https://mp.weixin.qq.com/s/2NoRkIKG0IFcoI-nZienAQ)  
**redis实现的话：** 热key的问题/数据会被删除；topic在kafka中更多是一个逻辑上的概念，实际存储单元都是partition；kafka用游标（cursor）  
**kafka在实际存储partition时又进行了一个拆分**：topicA-partition-0的数据并不是写到一个文件里，而是写到多个segment文件里,当segment中所有消息都过期时，可以很容易地直接删除整个文件。  
**为了防止kafka的index过大**，权衡之下kafka选择了使用”稀疏索引“。  

[总结 Kafka 背后的优秀设计](https://mp.weixin.qq.com/s/dfOP2MeBOqFqg_BdcJCYug)  
* 利用了 Page cache 来存储，这样躲开了数据在 JVM 因为 GC 而发生的 STW  
* 为了保证性能，Kafka 不会采用强一致性的方式来同步主从的数据。而是维护了一个：in-sync Replica 的列表，Leader 不需要等待所有 Follower 都完成同步  

[Linux Page Cache调优在Kafka中的应用](https://mp.weixin.qq.com/s/MaeXn-kmgLUah78brglFkg)  

[Kafka Exactly-Once 之事务性实现](http://matt33.com/2018/11/04/kafka-transaction/)  

[支持百万级TPS，Kafka是怎么做到的？](https://mp.weixin.qq.com/s/UeRLaoJyL6WOmvNfy5wujQ)  

[知乎基于Kubernetes的kafka平台的设计和实现](https://mp.weixin.qq.com/s/J6Rf0x2WQcGVWysf0R4-YA)  
