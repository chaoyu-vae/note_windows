### 常用命令

- ```shell
  #连接redis服务端
  redis-cli -h 127.0.0.1 -p 3306 -a  password
  ```

- ##### 链接：https://www.yiibai.com/redis/redis_keys.html

- ##### 键命令：

  ```shell
  get key #获取键对应的值
  set key value #设置键对应的值
  del key #删除指定的键(如果该键存在)
  exists key #判断键知否存在
  dump key #输出指定键对应值的序列化版本
  expire key seconds #设置键在指定秒后过期
  expireat key timestamp #设置键在指定时间戳后过期
  persist key #删除键的过期时间，变成永久有效
  pttl key #获取键的剩余到期时间
  rename key newkey #修改键名
  type key #返回键对应的值的存储类型
  mget key1 key2 #获取所有给定键的值
  setnx key value #当键不存在时，设置
  ```

- ##### 哈希命令

  ```shell
  hmset key field1 field2 #设置多个哈希散列
  hgetall key #获取该键对应的哈希散列
  hget key name #获取指定键中的哈希字段的值
  hkeys key #获取哈希中的所有字段
  hlen key #获取哈希字段数目
  hvals key #获取哈希中的所有值
  ```

- ##### redis列表(只是字符串列表)

  ```
  lpush key value #向列表中插入一个value，头插法
  lrange key start end #展示列表内容，但是需要指定开始和结束的下标
  llen key #获取列表的长度
  lpop key #删除列表第一个元素，并且返回该元素
  ```

### 底层基础

- #### SDS：简单动态字符串类型

  - 

### 实践出真知

- ##### 分布式锁：该条命令是原子操作，争抢设置锁然后为锁设置一个过期时间

  ```shell
  set key value nx ex time
  ```

- ##### keys命令：因为redis是单线程的所以到keys命令查出的内容很多的时候会导致线程阻塞一段时间，线上正好有业务进行的话。redis会不可用

- ##### scan命令能无阻塞的提取出指定模式的key列表

### 哨兵机制

- ##### 出现原因：解决主从复制出现故障时需要人为干预的问题

- ##### 功能：管理多个redis服务器，提供了监控、提醒和自动的故障转移功能
