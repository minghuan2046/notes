<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [ss](#ss)
	- [描述](#描述)
	- [命令参数](#命令参数)
	- [eg：](#eg)

<!-- /TOC -->

# ss

## 描述
Socket Statistics：即用于转储套接字统计信息

## 命令参数
    - n:不解析服务名称
    - r:解析主机名
    - a:显示所有套接字
    - l:显示监听状态的套接字
    - o：显示计时器信息
    - e:显示详细的套接字信息
    - m:显示套接字使用内存
    - p:显示使用套接字的进程
    - i：显示TCP内部信息
    - s：显示套接字使用情况
    - 4: 显示IPV4套接字信息
    - 6: 显示IPV6套接字信息
    - t:显示TCP的套接字信息
    - u：显示UDP套接字信息
    - x：显示unix套接字信息

## eg：
- 查看端口使用情况
```
ss
or lsof -i:port
```
- ss列出所有http连接中的连接
```
 ss -o state established '( dport = :http or sport = :http )'
```

- 查看与目标服务器连接
```
ss -p dst 10.237.8.100
```
