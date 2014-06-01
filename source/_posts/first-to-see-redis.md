title: 初识redis
date: 2014-02-15 18:22:06
tags: redis
---
最近在工作中用到了redis，觉得redis和mongo以及sql类的数据库差别还满大的，以本文来记录本人对redis的初步认识，可能有些不对的地方，欢迎指正。
<!--  more -->
## redis简介
### 优势
1. 非常非常的快，有测评说比Memcached还快(当大家都是单CPU的时候)，而且是无短板的快，读写都一般的快，所有API都差不多快，也没有MySQL Cluster、MongoDB那样更新同一条记录如Counter时慢下去的毛病。
1. 丰富的数据结构 : String / Hash / List / Set / Ordered Set。有丰富的api。相比sql类数据库只有table这种数据类型，mongoDB只有json这种数据结构
1. 因为是个人作品，Redis目前只有2.3万行代码，Keep it simple的死硬做法，使得普通公司而不需淘宝那个级别的文艺公司也可以吃透它。[Redis宣言](http://oldblog.antirez.com/post/redis-manifesto.html)就是作者的自白，“代码像首诗”，”设计是一场与复杂性的战斗“，“Coding是一件艰苦的事情，唯一的办法是享受它。如果它已不能带来快乐就停止它。为了防止这一天的出现，我们要尽量避免把Redis往乏味的路上带。”

### 不足
1. 单线程架构，使得代码不用处理平时最让人头痛的并发而大幅简化，但也带来CPU的瓶颈，而且单线程被慢操作所阻塞时，其他请求的延时变得不确定。
1. Redis 不是Big Data，数据都在内存中
1. Redis 不支持Ad-Hoc Query，提供的只是数据结构的API，没有SQL一样的查询能力

### 应用场景
1. 取最新N个数据的操作
1. 排行榜应用，取TOP N操作
1. 需要精准设定过期时间的应用
1. 计数器应用
1. Uniq操作，获取某段时间所有数据排重值
1. 实时系统，反垃圾系统
1. Pub/Sub构建实时消息系统
1. 构建队列系统
1. 缓存
    
[详情](http://blog.nosqlfan.com/html/2235.html)

### 数据类型    
(转自 http://www.cnblogs.com/lori/archive/2012/05/15/2501862.html)

1. string
> string是最简单的类型，你可以理解成与Memcached一模一样的类型，一个key对应一个value，其上支持的操作与Memcached的操作类似。但它的功能更丰富。    

1. hash
> Redis能够存储key对多个属性的数据（比如user1.uname user1.passwd），当然，你完成可以把这些属性以json格式进行存储，直接把它当作string类型进行操作，但这样性能上是对影响的，所以redis提出的Hash类型。    

1. list
> list是一个链表结构，主要功能是push、pop、获取一个范围的所有值等等。之所以说它是双向的，因为它可以在链表左，右两边分别操作

1. set
> set是集合，它是string类型的无序集合

1. zset
> zset是set的一个升级版本，他在set的基础上增加了一个顺序属性，这一属性在添加修改元素的时候可以指定，每次指定后，zset会自动重新按新的值调整顺序。 


## 下载安装
查看 http://redis.io/download。  
因为本屌丝目前用的是windows，所以介绍下windows下的下载安装。  
redis官方是不支持windows的。windows的非官方版本下载地址
 https://github.com/dmajkic/redis/downloads

解压后，根据计算机位数打开相应的文件夹。打开 redis-server.exe 和 redis-cli.exe。在redis-cli.exe里，对redis进行操作。

点这里查看[使用redis来做统计的例子](/2014/02/15/redis-demo1/)


## 资源
* http://blog.jobbole.com/44476/
* [在线try redis](http://try.redis.io/)
* [Redis little book](http://openmymind.net/2012/1/23/The-Little-Redis-Book)
* [Redis 命令参考(中文版)](http://www.redisdoc.com/en/latest/) 
* [Redis 命令参考(版)](http://www.redisdoc.com/en/latest/)
* http://blog.jobbole.com/44476/
* [Redis 设计与实现](http://www.redisbook.com/en/latest/)
* [Redis应用场景](http://blog.nosqlfan.com/html/2235.html)
* http://openmymind.net/2011/11/8/Redis-Zero-To-Master-In-30-Minutes-Part-1/



