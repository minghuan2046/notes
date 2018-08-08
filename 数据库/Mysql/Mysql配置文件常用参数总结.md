# 变量描述
## innodb_flush_log_at_trx_commit
#### 概述：控制着事务提交后日志刷盘的频率。可取值为0,1,2,默认值为1，属于全局动态变量。
- 当取值为0时，每一秒执行一次将Innodb log buffer写进日志文件并刷盘操作，当事务提交不执行任何操作，
  因此当mysqld进程崩溃可能导致一秒的数据丢失。
- 当取值为1时，表示完全符合ACID原则，每个事务提交，Innodb 的log buffer写进日志文件中并执行刷盘操作。
- 当取值为2时，表示每个事务提交，Innodb的log buffer写进日志文件，每一秒执行一次刷盘操作，因此当系统崩溃不会导致数据丢失，但可能会导致丢失1s的日志文件。

## innodb_io_capacity
#### 设置Innodb后台任务每秒执行的I/O操作数上限。最小值100，默认200，最大值2^64-1(2^32 -1)。这个数值控制着所有缓冲区实例的总数。可根据磁盘IO性能作相关调整。innodb_flush_sync配置选项会导致在检查点发生的I/O活动突发期间忽略innodb_io_capacity设置。innodb_flush_sync默认启用。

## innodb_io_capacity_max
####　如果刷盘操作落后，ＩnnoDB将刷盘限制将超越innodb_io_capacity的限制，此时innodb_io_capacity_max将起作用。启动时配置文件未申明大小，默认将被赋值为innodb_io_capacity大小的两倍，最小2000。

## innodb_buffer_pool_size   
缓存所有索引，数据。设置越高越降低取表数据是的硬盘I/O,一般设置为服务器物理内存的70%-80%，但是设置过大会导致物理内存竞争而导致系统分页。


## innodb_buffer_pool_instances
#### InnoDB缓冲池分区的区域数。当innodb_buffer_pool_size小于1G时则为1，当innodb_buffer_pool_size大于1G，默认8个。

## innodb_flush_method
#### 申明将数据写进数据文件和日志文件的方式，会影响I/O吞吐量.
-在Unix系统中，innodb_flush_method有如下取值：  
    fsync：InnoDB使用fsync()对数据和日志进行刷盘，fsync是默认值。
    O_DSYNC：InnoDB使用O_SYNC打开和冲刷日志文件，使用fsync()冲刷数据文件。
    littlesync：用于性能测试。
    nosync：不支持
    O_DIRECT：部分Linux系统支持
    O_DIRECT_NO_FSYNC：部分文件系统支持


## innodb_additional_mem_pool
#### 存放Innodb内部目录




## innodb_max_dirty_pages_pct
#### InnoDB从缓冲池中刷新数据，使脏页的百分比不超过此值。指定范围0-99，默认值75.

## innodb_max_dirty_pages_pct_lwm
#### 声明了一个脏页的"低水位线"，预刷新将开启。

## innodb_adaptive_flushing_lwm
#### 控制着redo log的"低水位线",当redo log百分比大于这个时将启用自适应刷盘策略

## innodb_flush_sync
