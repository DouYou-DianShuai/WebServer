# 对WebServer项目的学习
## 特性
- 利用Epoll与线程池实现Reactor高并发模型
- 利用状态机与正则实现HTTP请求报文解析，可同时处理GET与POST请求
- 用vector容器封装char，实现了一个可自动扩容的缓冲区
- 基于epoll_wait实现定时功能，关闭超时的非活动连接，并用小根堆作为容器管理定时器
- 加入线程池，减小线程创建与销毁的开销
- 利用MySQL的数据库连接池，减少数据库连接建立与关闭的开销，实现了用户注册登录功能
- 利用单例模式与阻塞队列实现异步日志系统，记录服务器运行状态
  

## 项目启动
`先看一下目录`
```
.
├── build
│   └── Makefile
├── code
│   ├── buffer
│   ├── http
│   ├── lock
│   ├── log
│   ├── main.cpp
│   ├── server
│   ├── sqlconnpool
│   ├── threadpool
│   └── timer
├── Makefile
├── README.md
└── resources
```

`1.先配置好数据库`
```
//创建数据库
create database webdb;
//创建user表
USE yourdb;
CREATE TABLE user(
    username char(50) NULL,
    passwd char(50) NULL
)ENGINE=InnoDB;
```
配置好后，修改main中对应函数参数。

`2.编译运行`
```
make   //直接执行外部的Makefile--它会创建serverbin目录并间接调用build的Makefile
./serverbin/WebServer
```
`3.通过浏览器访问`

（代码中绑定端口8888）

## 项目展示

* 首页
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E9%A6%96%E9%A1%B5.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E9%A6%96%E9%A1%B5.png)

****

* 登陆页面测试
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E7%99%BB%E5%BD%95%E9%A1%B5%E9%9D%A2%E6%B5%8B%E8%AF%95.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E7%99%BB%E5%BD%95%E9%A1%B5%E9%9D%A2%E6%B5%8B%E8%AF%95.png)

****

* 注册页面测试
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E6%B3%A8%E5%86%8C%E9%A1%B5%E9%9D%A2%E6%B5%8B%E8%AF%95.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E6%B3%A8%E5%86%8C%E9%A1%B5%E9%9D%A2%E6%B5%8B%E8%AF%95.png)

****

* 登陆或注册成功
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E7%99%BB%E5%BD%95%E6%88%96%E6%B3%A8%E5%86%8C%E6%88%90%E5%8A%9F.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E7%99%BB%E5%BD%95%E6%88%96%E6%B3%A8%E5%86%8C%E6%88%90%E5%8A%9F.png)

****

* 登陆或注册失败
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E7%99%BB%E5%BD%95%E6%88%96%E6%B3%A8%E5%86%8C%E5%A4%B1%E8%B4%A5.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E7%99%BB%E5%BD%95%E6%88%96%E6%B3%A8%E5%86%8C%E5%A4%B1%E8%B4%A5.png)

****

* 图片测试页面
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E5%9B%BE%E7%89%87%E6%B5%8B%E8%AF%95%E9%A1%B5%E9%9D%A2.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E5%9B%BE%E7%89%87%E6%B5%8B%E8%AF%95%E9%A1%B5%E9%9D%A2.png)

****

* 视频测试页面
  
<!-- ![image](https://github.com/DouYou-DianShuai/WebServer/blob/main/picture/%E8%A7%86%E9%A2%91%E6%B5%8B%E8%AF%95%E9%A1%B5%E9%9D%A2.png) -->

![image](https://gitee.com/DouYou-DianShuai/WebServer/raw/main/picture/%E8%A7%86%E9%A2%91%E6%B5%8B%E8%AF%95%E9%A1%B5%E9%9D%A2.png)

****
### 致谢

[markparticle/WebServer](https://github.com/markparticle/WebServer)

