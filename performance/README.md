# 性能优化

遇到性能瓶颈的排查思路：

有监控的情况下，首先去看看监控大盘，看看有没有异常报警，如果初期还没有监控的情况我会按照下面步骤去看看系统层面有没有异常

1. 我首先会去看看系统的平均负载，使用top或者htop命令查看,平均负载体现的是系统的一个整体情况，他应该是cpu、内存、磁盘性能的一个综合，一般是平均负载的值大于机器cpu的核数，这时候说明机器资源已经紧张了
2. 平均负载高了以后，接下来就要看看具体是什么资源导致，我首先会在top中看cpu每个核的使用情况，如果占比很高，那瓶颈应该是cpu,接下来就要看看是什么进程导致的
3. 如果cpu没有问题，那接下来我会去看内存，首先是用free去查看内存的是用情况，但不直接看他剩余了多少，还要结合看看cache和buffer，然后再看看具体是什么进程占用了过高的内存，我也是是用top去排序
4. 内存没有问题的话就要去看磁盘了，磁盘我用iostat去查看，我遇到的磁盘问题比较少
5. 还有就是带宽问题，一般会用iftop去查看流量情况，看看流量是否超过的机器给定的带宽
6. 涉及到具体应用的话，就要根据具体应用的设定参数来查看，比如连接数是否查过设定值等
7. 如果系统层各个指标查下来都没有发现异常，那么就要考虑外部系统了，比如数据库、缓存、存储等

##　CPU性能

1. [CPU性能 ---- 基础](1.cpu_1.md)
2. [CPU性能 ---- 案例](1.cpu_２.md)
3. [CPU性能 ---- 模式](1.cpu_３.md)
