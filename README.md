# 使用说明
+ libpcap-1.9.1.tar.gz和tcpdump-4.9.3.tar.gz是源码包
+ 目录里是已经编译安装完成的，不需要执行
```shell
./configure
make
make install
```
+ 如果想要重新编译的可以自行执行
## 使用步骤
- 进入tcpdump-4.9.3目录
```shell
./tcpdump -i eth0 -C 100 -w /root/info.pcap
```
- -i 指定网口
- -C 指定单个包的大小为多少M
- -w 指定包的存放路径
- info.pcap 包名，必须以.pcap结尾

- -i any 监听所有的网卡接口，用来查看是否有网络流量
- -i eth0 只监听eth0网卡接口
- -D 显示可用的接口列表
- -n 不要解析主机名
- -nn 不要解析主机名或者端口名
- -q 显示更少的输出(更加quiet)
- -t 输出可读的时间戳
- -tttt 输出最大程度可读的时间戳
- -X 以hex和ASCII两种形式显示包的内容
- -XX 与**-X**类似，增加以太网header的显示
- -v, -vv, -vvv 显示更加多的包信息
- -c 只读取x个包，然后停止
- -s 指定每一个包捕获的长度，单位是byte，使用-s0可以捕获整个包的内容
- -S 输出绝对的序列号
- -e 获取以太网header
- -E 使用提供的秘钥解密IPSEC流量

## 示例

### 1、捕获网卡流量
#### 1.1捕获所有流量
```shell
tcpdump -i any
```
#### 1.2捕获指定网口流量
```shell
tcpdump -i eth0
```

### 2、基于IP查找流量
最重要的查询方式之一就是host，我们可以使用如下命令查看IP 1.1.1.1 上的进出流量：
```shell
tcpdump host 1.1.1.1
```

### 3、根据源和目标进行过滤
如果只想要看单一方向的流量，可以使用src或者dst：
```shell
tcpdump src 1.1.1.1
tcpdump dst 1.0.0.1
```

### 4、根据网段查找
如果想要查看某一网段或者子网的进出流量，可以使用如下命令：
```shell
tcpdump net 1.2.3.0/24
```

### 5、使用十六进制输出
当我们想要检查包的内容是否有问题时，十六进制的输出很有帮助：
```shell
tcpdump -c 1 -X icmp
```

### 6、显示特定端口的流量
可以使用port查看特定端口的流量：
```shell
tcpdump port 3389
tcpdump src port 1025
```

### 7、显示特定协议的流量
如果想要查看特定协议的流量，你可以使用tcp、udp、icmp等各种协议：
```shell
tcpdump icmp
```

### 8、只显示ipv6的流量
通过协议参数可以查看所有ipv6的流量：
```shell
tcpdump ip6
```

### 9、查看一个端口段的流量
查看某一范围内的所有端口的流量：
```shell
tcpdump portrange 21-23
```

### 10、基于包大小进行筛选
如果你正在查看特定大小的包，你可以使用这个参数。使用 less、greater 或者对应的数学符号进行过滤：
```shell
tcpdump less 32 
tcpdump greater 64 
tcpdump <= 128
```

### 11、读写文件
#### 11.1、使用-w将结果保存为文件
```shell
tcpdump port 80 -w capture_file
```
#### 11.2、使用-r读取保存的文件
```shell
tcpdump -r capture_file
```


## 备注
- 也可以只下载tcpdump进行使用
```shell
https://github.com/lichuang69316/tcpdump/blob/master/tcpdump-4.9.3/tcpdump
```
![image.png](https://i.loli.net/2020/04/24/NiOe7mWlarpFUqg.png)

