title: 读书笔记之linux内核参数优化
tags:
  - Nginx
  - linux
  - 优化
categories:
  - 读书笔记
date: 2016-01-18 21:44:00
---
当你使用Nginx的时候可能会涉及到一些linux内核的优化，以满足高并发访问的需求。

<!-- more -->

优化内核的时候，可以做的事情很多，不过，我们通常会根据业务特点来进行调整。不同业务，不同场景，其内核参数的调整都是不同的。这里只针对最通用的,使Nginx支持更多的并发请求的TCP网络参数做简单说明。

首先，需要修改/etc/sysctl.conf来更改内核参数。列如，最常用的配置：


![配置文件](/images/2E61ED06-0253-4FE2-A938-A6BBF551A73F.png)


然后执行sysctyl -p命令，使上述修改生效。


上面的参数意义解释如下：


file-max : 这个参数表示进程(比如一个worker进程)可以同时打开的最大句柄数，这个参数直接限制最大并发连接数，需根据实际情况配置。

tcp_tw_reuse:  这个参数设置为1，表示允许将TIME—WAIT状态的socket重新用于将的TCP连接，这对于服务器来说很有意义，因为服务器上总会有大量的TIME-WAIT状态的连接。


其它参数可以参考如下图：
![参数解释](/images/79791022-ADA0-4D8E-A1C3-867C611C11AE.png)

------------------

更多书籍读书笔记请参看

https://github.com/edagarli/ReadingNotes
