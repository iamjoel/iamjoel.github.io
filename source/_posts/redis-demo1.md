title: 使用redis来做统计的例子
date: 2014-02-15 20:09:37
tags: redis
---
## 使用redis来做统计的简单例子
使用redis来完成如下功能
1. 统计某天的上线人数
1. 统计用户一日的流失(下线后，第二天未上线的)
<!--  more -->

### 设计schema    
上线：    
key： `online:{YYYY-MM-DD}`       
value：userId    
下线：     
key： `offline:{YYYY-MM-DD}`     
value：userId      
数据类型为set  

### 采集数据 
#### 采集用户上线数据
每次用户上线时，在上线的数据中加入上线用户的userId。    
例如，如果‘joel’在2014年1月1日上线，那么执行 
`sadd 'online:2014-01-01' joel` 
#### 采集用户下线数据  
每次用户下线时，在下线的数据中加入下线用户的userId。

### 数据统计
#### 统计某天的在线人数
例如 统计2014-01-01的。 执行  
`scard 'online:2014-01-01'`

#### 统计某天的用户一日的流失
例如 统计2014-01-01的。 那么取2013-12-31下线和2014-01-01上线的交集。执行 
 `sinter 'offline:2013-12-31' 'online:2014-01-01'` 然后取结果集的长度

基于nodejs的实现的完整源码[点这里](https://github.com/iamjoel/node-test/tree/master/redis-simple)



