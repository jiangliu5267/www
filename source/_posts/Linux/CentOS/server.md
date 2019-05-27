---
title: 换新系统之腾讯云学生机 CentOS 7.6 64 位
date: 2019-5-9 18:22:34
tags:
  - CentOS
  - server
count: 1
os: 0
os_1: 10.0.17763.437 2019-LTSC
browser: 0
browser_1: 72.0.3626.121 Stable
place: 家
key: 50
---
    然后原来的一元机就换系统了……
<!-- more -->

## 0x00.修改主机名
``` bash
[root@txy ~]# hostnamectl set-hostname txy.yuangezhizao.cn
[root@txy ~]# cat /etc/hosts 
127.0.0.1 txy.yuangezhizao.cn txy.yuangezhizao.cn
127.0.0.1 localhost.localdomain localhost
127.0.0.1 localhost4.localdomain4 localhost4

::1 txy.yuangezhizao.cn txy.yuangezhizao.cn
::1 localhost.localdomain localhost
::1 localhost6.localdomain6 localhost6
```

## 0x01.更新
``` bash
yum update
```

## 0x02.软件
1. `nfs-utils`：暂时`10G`免费
![腾讯云文件系统](https://i1.yuangezhizao.cn/Win-10/20190509232645.jpg!webp)


2. `htop`
3. `git`
4. `axel`：多线程下载工具
5. `COSFS`：https://github.com/tencentyun/cosfs
![直接在本地是相当爽了，可惜 Win 享受不到](https://i1.yuangezhizao.cn/Win-10/20190509232817.jpg!webp)

## 0x03.挂载第三方存储
1. 腾讯云文件存储即`CFS`
2. 腾讯云对象存储即`COS`
![白嫖的一年资源包](https://i1.yuangezhizao.cn/Win-10/20190509233243.jpg!webp)
![最终效果可以说是相当爽了](https://i1.yuangezhizao.cn/Win-10/20190509224926.jpg!webp)

## 0x04.编译安装[python373](https://www.python.org/downloads/release/python-373/)环境
1. 查看现有位置
``` bash
[root@txy ~]# whereis python
python: /usr/bin/python /usr/bin/python2.7 /usr/lib/python2.7 /usr/lib64/python2.7 /etc/python /usr/include/python2.7 /usr/share/man/man1/python.1.gz
```
2. 安装编译工具
``` bash
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel
```
> 这里面有一个包很关键`libffi-devel`，因为只有`3.7`才会用到这个包，如果不安装这个包的话，在`make`阶段会出现如下的报错：`# ModuleNotFoundError: No module named '_ctypes'`

3. 下载源码包
奇怪的是我用`IDM`本地多线程下载的包，传上去解压的时候会报错，查了下说是包不完整需要重下，无奈……
`==`
只能`wget`龟速下载了……
``` bash
wget --no-check-certificate https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz
```
4. 解压
``` bash
tar -zxvf Python-3.7.0.tgz
cd Python-3.7.0
```
5. 编译
``` bash
sudo ./configure --prefix=/usr/local/python3
sudo make && make install
```
6. 安装`pip3`
``` bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```
7. 升级`pip3`
``` bash
[root@txy ~]# pip3 install --upgrade pip
Looking in indexes: http://mirrors.tencentyun.com/pypi/simple
Requirement already up-to-date: pip in /usr/local/python3/lib/python3.7/site-packages (19.1.1)
```
8. 创建软链接（`python3`&`pip3`）
``` bash
sudo ln -s /usr/local/python3/bin/python3 /usr/bin/python3
sudo ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip3
[root@txy ~]# python -V
Python 2.7.5
[root@txy ~]# python3 -V
Python 3.7.3
```
> 这样就可以通过`python`命令使用`Python 2`，`python3`来使用`Python 3`。

9. 更改`yum`配置
``` bash
vim /usr/bin/yum 
vim /usr/libexec/urlgrabber-ext-down 
vim /bin/yum-config-manager
```
把`#! /usr/bin/python`修改为`#! /usr/bin/python2`
10. 修改默认为`Python 3`
将`/usr/bin`中的`python`备份，然后创建`python3`的软链接，这样默认的`Python`版本就替换为`Python 3`了。
``` bash
[root@txy ~]# sudo mv /usr/bin/python /usr/bin/python.bak
[root@txy ~]# sudo ln -s /usr/local/python3/bin/python3 /usr/bin/python
```
11. 加入环境变量
`vim ~/.bash_profile`
`PATH=$PATH:$HOME/bin:/usr/local/python3/bin`

## 0x05.安装[Docker](https://docs.docker.com/install/linux/docker-ce/centos/)
1. 卸载旧版本
``` bash
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```
2. 使用源安装
`sudo yum install -y yum-utils device-mapper-persistent-data lvm2`
`sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo`
3. 安装
`sudo yum install docker-ce docker-ce-cli containerd.io`
4. 启动
`sudo systemctl start docker`
5. 测试
`sudo docker run hello-world`
输出如下：
``` bash
[root@txy ~]# docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete 
Digest: sha256:6f744a2005b12a704d2608d8070a494ad1145636eeb74a570c56b94d94ccdbfc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```
6. 加速器
`curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://e6d6fb48.m.daocloud.io`
7. 自启
`sudo systemctl enable docker`

## 0x06. 测速工具`speedtest-cli`
`pip3 install speedtest-cli`
``` bash
[root@txy ~]# speedtest-cli
Retrieving speedtest.net configuration...
Testing from Tencent cloud computing (<rm>)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Beijing Unicom (Beijing) [1.69 km]: 28.199 ms
Testing download speed................................................................................
Download: 86.21 Mbit/s
Testing upload speed......................................................................................................
Upload: 1.27 Mbit/s
```