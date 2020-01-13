### redis学习 ###
Redis 是完全开源免费的，遵守BSD协议，是一个高性能的key-value数据库。

#### 常用数据结构 ####
String: 字符串 set get
Hash: 散列 hmset hget
List: 列表 lpush lrange
Set: 集合 sadd smembers
Sorted Set: 有序集合 zadd zrangebyscore


- 发布订阅    
>  异步消息通知    
  任务通知 定时任务        
  参数刷新加载 缓存参数更新通知    

- 事务
> watch multi  乐观锁


- 持久化
> RDB: 数据快照,实时性较差
> AOF: 日志方式,实时保存

持久化
当redis退出时会触发持久化操作,如果想要恢复持久化数据,rdb的话只需要将持久化文件放到redis的工作目录即可.查看工作目录方式:
> config get dir

同时config set dir 可以设置持久化文件目录
  

#### 编码类型 ####

list 5.0.7版本缺少list-max-ziplist-entries参数


#### 兴趣点 ####

- 读写测试

Redis能读的速度是110000次/s,写的速度是81000次/s 


- docker compose 进行端口映射但是进入容器时,连接拒绝,但是6379可以使用

docker exec -ti redis redis-cli -h localhost -p 8081

- docker 复制文件到host,容器和host目录绑定

docker inspect redis|grep /var/lib/docker/volumes
docker-compose的volume挂载是在/var/lib/docker/volumes目录下的挂载目录的定义,不是常规的本地文件挂载,本地文件挂载应该使用bind.但是由于挂载点重复,我没有bind成功

- key命名规范
	库:表:数据

- sort命令,debug追踪

- 主从复制,主节点异常时处理



- 数据一致性
问题没有复制文件到镜像中,所以总是提示找不到文件

- docker权限
docker文件具有权限限制,直接复制文件时要注意,否则可能造成文件无法加载的问题

#### 参考资料 ####

- 生产中如何使用发布订阅 https://blog.csdn.net/ibigboy/article/details/95751542

