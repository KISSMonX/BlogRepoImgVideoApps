## 一. 收集的文章

#### 1. [日访问量百亿级的应用如何做缓存架构设计](https://blog.didiyun.com/index.php/2018/05/22/weibo-cache/)  

> 新浪微博技术专家陈波为大家讲解了**微博Cache架构的设计实践过程。**

#### 2. [微服务系统之认证管理详解](https://mp.weixin.qq.com/s/PRSbOYVX-aBmp7S_0qYeuQ)  

> 微服务大行其道，微服务安全也是非常热门的话题。本文向大家分享微服务系统中认证管理相关技术。其中包括用户认证、网关和 API 认证、系统间和系统内的认证，以及我们的统一认证管理系统 IAM。 

#### 3. [10 分钟理解什么是 OAuth 2.0 协议](https://deepzz.com/post/what-is-oauth2-protocol.html)     

> OAuth 2.0 是一个行业的标准授权协议。OAuth 2.0 专注于简化客户端开发人员，同时为 Web 应用程序，桌面应用程序，手机和客厅设备提供特定的授权流程。
>
> 它的最终目的是为第三方应用颁发一个有时效性的令牌 token。使得第三方应用能够通过该令牌获取相关的资源。常见的场景就是：第三方登录。当你想要登录某个论坛，但没有账号，而这个论坛接入了如 QQ、Facebook 等登录功能，在你使用 QQ 登录的过程中就使用的 OAuth 2.0 协议。


#### 4. [Go 空死循环导致的调度器无法调度](https://rakyll.org/scheduler/)     


```golang

package main

import (
	"log"
	"runtime"
	// "time"
)

func main() {
	runtime.GOMAXPROCS(4)
	ch := make(chan bool)

	go func() {
		for {
			ch <- true
			log.Println("sent")
		}
	}()

	go func() {
		for {
			re := <-ch
			log.Println("received:", re)
		}
	}()

	// 运行一段时间会卡死
	for {
		// log.Println("=========Deadloop========")
		// time.Sleep(time.Second)
	}
}

```

还可参考:   
- [https://gocn.vip/question/2116](https://gocn.vip/question/2116)  
- [https://github.com/golang/go/issues/15442](https://github.com/golang/go/issues/15442)  


#### 5. [一篇好TM长的关于配置中心的文章](http://jm.taobao.org/2016/09/28/an-article-about-config-center/)  

> 讲述了配置中心出现的必然, 论证了大型分布式系统是必须配置中心的, 并且配置中心需要有导入导出功能, 以及配置中心和注册中心的区别. 



#### 6. [如何实现靠谱的分布式锁？](https://mp.weixin.qq.com/s?__biz=MzIwMzg1ODcwMw==&mid=2247488347&idx=1&sn=057fb356decaf3cbf703d7ab600f8d3b&chksm=96c9a53ba1be2c2d7a530ef02bcd9eb1f1bef91c29473abecab8e568a065882961e6210d6307&mpshare=1&scene=1&srcid=0825XVuWFKkAvRpbtak3o8oV#rd)

> 分布式锁，是用来控制分布式系统中互斥访问共享资源的一种手段，从而避免并行导致的结果不可控。基本的实现原理和单进程锁是一致的，通过一个共享标识来确定唯一性，对共享标识进行修改时能够保证原子性和和对锁服务调用方的可见性。由于分布式环境需要考虑各种异常因素，为实现一个靠谱的分布式锁服务引入了一定的复杂度。



#### 7. [什么是缓存击穿](http://blog.jobbole.com/114012/)

> 如果黑客每次故意查询一个在缓存内必然不存在的数据，导致每次请求都要去存储层去查询，这样缓存就失去了意义。如果在大流量下数据库可能挂掉。这就是缓存击穿。



#### 8. [Dapper: 大规模分布式系统的跟踪系统](https://bigbully.github.io/Dapper-translation/)

> Dapper--Google生产环境下的分布式跟踪系统，应运而生。那么我们就来介绍一个大规模集群的跟踪系统，它是如何满足一个低损耗、应用透明的、大范围部署这三个需求的

#### 9. [常见性能优化策略的总结](https://tech.meituan.com/performance_tunning.html)

> 数据库， 缓存， 异步处理， NoSQL， 多线程， 分布式， 度量系统， 优化还涉及前端、分布式文件系统、CDN、全文索引、空间索引等几方面。

#### 10. [前端遇上Go: 静态资源增量更新的新实践](https://tech.meituan.com/fe_and_golang.html)

> 在我们的新实践中，都有哪些大家可以真正借鉴的点：
>
> 1. 不同的语言和工具有不同的用武之地，不要试图用锤子去锯木头。该换语言就换，不要想着一个语言或工具解决一切。
> 2. 更换语言是一个重要的决定，在决定之前首先需要思考是否应当这么做。
> 3. 语言解决更多的是局部问题，架构解决更多的是系统问题。换了语言也不代表就万事大吉了。
> 4. 构建一个系统时，首先思考它是如何垮的。想清楚你的系统潜在瓶颈会出现在哪，如何加强它，如何考虑它的备用方案。

#### 11. [Redis 高负载下的中断优化](https://tech.meituan.com/Redis_High_Concurrency_Optimization.html)

> 原本稳定的环境也因为请求量的上涨带来了很多不稳定的因素，其中一直困扰我们的就是网卡丢包问题。起初线上存在部分Redis节点还在使用千兆网卡的老旧服务器，而缓存服务往往需要承载极高的查询量，并要求毫秒级的响应速度，如此一来千兆网卡很快就出现了瓶颈。经过整治，我们将千兆网卡服务器替换为了万兆网卡服务器，本以为可以高枕无忧，但是没想到，在业务高峰时段，机器也竟然出现了丢包问题，而此时网卡带宽使用还远远没有达到瓶颈。

#### 12. [境外业务性能优化实践](https://tech.meituan.com/Overseas_%20business_performance%20_optimization_%20practice.html)

> 如何提升产品性能，做到像国内业务一样，其中面临了很多的技术挑战。本文将从网络优化、前端优化、后端优化几个方面来介绍境外业务在性能优化方面的做过的一些事情。



## 二. 收集的图片

#### 1. 各种排序算法的时间复杂度

---

![排序时间复杂度](./images/sorters.png)

---

#### 2. TCP 状态转移图, 重点 TIME\_WAIT, CLOSE\_WAIT

![TCP状态图](./images/TCPState.jpg)

---

#### 3. TCP 三次握手, 四次挥手

![TCP握手挥手](./images/TCPShakeBye.jpg)

---


## 三. 收集的仓库 

####  1. [Go夜读群的总结分享](https://github.com/developer-learning/night-reading-go)    

> 好多文章和仓库, 都是从这个群交流后收集的, 感谢分享, 感谢开源.


#### 2. [系统设计技能树](https://github.com/donnemartin/system-design-primer/blob/master/README-zh-Hans.md)    

> 系统设计相关, 感觉是架构师, 系统工程师必备的技能树

#### 3. [Codis: Proxy based Redis cluster solution supporting pipeline and scaling dynamically](https://github.com/CodisLabs/codis)

> Codis 是一个分布式 Redis 解决方案, 对于上层的应用来说, 连接到 Codis Proxy 和连接原生的 Redis Server 没有显著区别 (不支持的命令列表), 上层应用可以像使用单机的 Redis 一样使用, Codis 底层会处理请求的转发, 不停机的数据迁移等工作, 所有后边的一切事情, 对于前面的客户端来说是透明的, 可以简单的认为后边连接的是一个内存无限大的 Redis 服务。


#### 4. [Pika: is a nosql compatible with redis, it is developed by Qihoo's DBA and infrastructure team](https://github.com/Qihoo360/pika)

> Pika是一个可持久化的大容量redis存储服务，兼容string、hash、list、zset、set的绝大部分接口(兼容详情)，解决redis由于存储数据量巨大而导致内存不够用的容量瓶颈，并且可以像redis一样，通过slaveof命令进行主从备份，支持全同步和部分同步，pika还可以用在twemproxy或者codis中来实现静态数据分片

#### 5. [Qconf: Qihoo Distributed Configuration Management System](https://github.com/Qihoo360/QConf)

> QConf 是一个分布式配置管理工具。 用来替代传统的配置文件，使得配置信息和程序代码分离，同时配置变化能够实时同步到客户端，而且保证用户高效读取配置，这使的工程师从琐碎的配置修改、代码提交、配置上线流程中解放出来，极大地简化了配置管理工作。


#### 6. [Beats - Lightweight shippers for Elasticsearch & Logstash](https://github.com/elastic/beats)

> 基于 Golang 的轻量级日志采集软件, 包括: 文件, 流量等等...

#### 7. [Jaeger - a Distributed Tracing System](https://github.com/jaegertracing/jaeger)

> It can be used for monitoring microservices-based distributed systems:
>
> - Distributed context propagation
> - Distributed transaction monitoring
> - Root cause analysis
> - Service dependency analysis
> - Performance / latency optimization

#### 8. [ Pholcus is a distributed, high concurrency and powerful web crawler software.](https://github.com/henrylee2cn/pholcus)

> 1. 为具备一定Go或JS编程基础的用户提供只需关注规则定制、功能完备的重量级爬虫工具；
> 2. 支持单机、服务端、客户端三种运行模式；
> 3. GUI(Windows)、Web、Cmd 三种操作界面，可通过参数控制打开方式；
> 4. 支持状态控制，如暂停、恢复、停止等；
> 5. 可控制采集量；
> 6. 可控制并发协程数；
> 7. 支持多采集任务并发执行；
> 8. 支持代理IP列表，可控制更换频率；
> 9. 支持采集过程随机停歇，模拟人工行为；
> 10. 根据规则需求，提供自定义配置输入接口
> 11. 有mysql、mongodb、kafka、csv、excel、原文件下载共五种输出方式；
> 12. 支持分批输出，且每批数量可控；
> 13. 支持静态Go和动态JS两种采集规则，支持横纵向两种抓取模式，且有大量Demo；
> 14. 持久化成功记录，便于自动去重；
> 15. 序列化失败请求，支持反序列化自动重载处理；
> 16. 采用surfer高并发下载器，支持 GET/POST/HEAD 方法及 http/https 协议，同时支持固定UserAgent自动保存cookie与随机大量UserAgent禁用cookie两种模式，高度模拟浏览器行为，可实现模拟登录等功能；
> 17. 服务器/客户端模式采用Teleport高并发SocketAPI框架，全双工长连接通信，内部数据传输格式为JSON。

#### 9. [Colly: Elegant Scraper and Crawler Framework for Golang](https://github.com/gocolly/colly)

> ## Features
>
> - Clean API
> - Fast (>1k request/sec on a single core)
> - Manages request delays and maximum concurrency per domain
> - Automatic cookie and session handling
> - Sync/async/parallel scraping
> - Caching
> - Automatic encoding of non-unicode responses
> - Robots.txt support
> - Distributed scraping
> - Configuration via environment variables
> - Extensions


## 四. 收集的视频

## 五. 收集的工具软件

#### 1. [Vertabelo](http://www.vertabelo.com/features)

> 能做逻辑关系的数据库 model 设计软件

#### 2. [Kibana Online Demo](https://demo.elastic.co/app/kibana)

> 可以用来自己作图参考, 有些好看的图, 可以参考 demo 来做. 

#### 3. [yulong-hids: 一款由 YSRC 开源的主机入侵检测系统](https://github.com/ysrc/yulong-hids)

> - 实时监控、秒级响应
> - 全局首次出现概念，可发现未知威胁
> - 支持自定义规则，高扩展性
> - 高级分析功能，可溯源
> - 全局快速阻断（进程、文件）
> - 威胁情报查询（可自定义接口）

#### 4. [YApi 是一个可本地部署的、打通前后端及QA的、可视化的接口管理平台](https://github.com/YMFE/yapi)

> ### 特性
>
> - 基于 Json5 和 Mockjs 定义接口返回数据的结构和文档，效率提升多倍
> - 扁平化权限设计，即保证了大型企业级项目的管理，又保证了易用性
> - 类似 postman 的接口调试
> - 自动化测试, 支持对 Response 断言
> - MockServer 除支持普通的随机 mock 外，还增加了 Mock 期望功能，根据设置的请求过滤规则，返回期望数据
> - 支持 postman, har, swagger 数据导入
> - 免费开源，内网部署，信息再也不怕泄露了