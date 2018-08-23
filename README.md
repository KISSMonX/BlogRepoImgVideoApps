## 一. 收集的文章

#### 1. [日访问量百亿级的应用如何做缓存架构设计](https://blog.didiyun.com/index.php/2018/05/22/weibo-cache/)  



#### 2. [微服务系统之认证管理详解](https://mp.weixin.qq.com/s/PRSbOYVX-aBmp7S_0qYeuQ)  


#### 3. [10 分钟理解什么是 OAuth 2.0 协议](https://deepzz.com/post/what-is-oauth2-protocol.html)     


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


## 二. 收集的图片



## 三. 收集的仓库 

####  1. [Go夜读群的总结分享](https://github.com/developer-learning/night-reading-go)    

> 好多文章和仓库, 都是从这个群交流后收集的, 感谢分享, 感谢开源.
  
  
#### 2. [系统设计技能树](https://github.com/donnemartin/system-design-primer/blob/master/README-zh-Hans.md)    

> 系统设计相关, 感觉是架构师, 系统工程师必备的技能树





