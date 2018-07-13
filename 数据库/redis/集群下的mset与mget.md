#### 1.mset
##### 正确使用eg:
```
 cluster.mset("{" + prefix + KEY_SPLIT + "}"+"name", "张三",
                "{" + prefix + KEY_SPLIT + "}"+"age", "23",
                "{" + prefix + KEY_SPLIT + "}"+ "address", "adfsa")
```
其中由prefix，KEY_SPLIT组成hash tag，用这两个值作hash计算，这两个值相同的key将分布到同一个slot，因此可能造成数据分布不均的情况，请视情况选择使用。
##### 错误使用：
```
cluster.mset("name", "张三",
              "age", "23"）
```
原因：没提供hash tag无法确定分布到同一分片。  
redis-cli报错信息:LOT Keys in request don't hash to the same slot

jedis报错信息：No way to dispatch this command to Redis Cluster because keys have different slots.
#### 2.mget
##### 正确使用eg：
```
list = cluster.mget("{" + prefix + KEY_SPLIT + "}" + "name",
                "{" + prefix + KEY_SPLIT + "}" + "age"）
```
##### 错误使用：
```
list = cluster.mget（"name",
                     "age"）
```
报错理由同mset  
redis-cli报错信息:(error) CROSSSLOT Keys in request don't hash to the same slot

jedis报错信息：No way to dispatch this command to Redis Cluster because keys have different slots.
#### 3.jedis
官方API不支持集群的Pipline操作，目前网上有部分人通过代码实现了自定义的集群Pipline操作，但均有一些限制，具体性能未验证。
