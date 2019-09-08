## 简介

这个软件是一个基于UPD协议的发包机器。该软件使用Go语言进行编写，得益于Go语言高效的Goroutine机制，可以轻松实现并发多了客户端同时像服务端发送请求。

测试服务器的硬件配置为: 32g memory Intel(R) Xeon(R) CPU E5-2670 0 @ 2.60GH.

测试实验时启动了18个协程，并发送64B的UDP包。

测试结果如图所示
![image](https://github.com/w910820618/picture_repo/blob/master/1567492469993.png)

## 安装和使用说明

### 安装

```
cd  $GOPATH/src
git clone https://github.com/yunshoutech/thunder.git
cd thunder 
go build *.go
chmod 777 ./client
```

### 使用说明

- 服务端

```
./client -s -h 127.0.0.1
```

 -s 是否启动服务器端，默认为否

-h 服务端绑定的IP地址，默认为127.0.0.1

- 客户端

```
./client -h 127.0.0.1 -n 18 -d 2000s -len 64B
```

-h 目标服务端地址，默认为：127.0.0.1

-n 启动协程的数量

-d 程序运行时间

-len UDP包的长度

