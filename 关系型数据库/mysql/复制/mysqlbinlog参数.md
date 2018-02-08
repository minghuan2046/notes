# 用法
mysqlbinlog [option] file

- '--short-form':只打印被执行的SQL语句信息，忽略关于二进制日志中事件的注释信息。
- '--force-if-open':如果binlog没有被正确关闭，无论因为binlog文件仍被写入还是因为服务器崩溃，mysqlbinlog都将打印一条警告说这个binlog文件没有被正确关闭，该选项是为了防止该条警告
- '--base64-output=nerver':阻止mysqlbinlog打印base64-encodeed事件
