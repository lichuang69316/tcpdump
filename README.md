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
## 备注
- 也可以只下载tcpdump进行使用
```shell
https://github.com/lichuang69316/tcpdump/blob/master/tcpdump-4.9.3/tcpdump
```
![image.png](https://i.loli.net/2020/04/24/NiOe7mWlarpFUqg.png)

