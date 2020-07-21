# 常用命令

| 操作                 | 命令                              |
| -------------------- | --------------------------------- |
| 安装平台依赖         | yum install                       |
| 查看当前文件夹下文件 | ls                                |
| 下载文件             | wget [url：文件资源地址]          |
| 解压文件             | tar -zxvf  [path：文件路径]       |
| 复制文件             | mv [当前目录文件]  [目标文件路径] |
| 查找文件             | find / -name [文件名称]           |
|                      |                                   |



# 下载安装mongodb

**1.开始**

```
// 安装Linux平台依赖包
yum install libcurl openssl
// 下载
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-ubuntu1604-4.2.8.tgz 

// 解压
tar -zxvf mongodb-linux-x86_64-ubuntu1604-4.2.8.tgz 
// 拷贝
mv mongodb-src-r4.2.8  /usr/local/mongodb4 
// 添加path
export PATH=/usr/local/mongodb4/bin:$PATH

mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --fork

// 打开mongodb数据库
mongo
```

**2.快速启动**

也可以在指定位置创建启动配置文件 通过配置文件打开mongodb服务

在/usr/local/mongodb4目录下递归创建文件夹 data/db/log 及文件mongod.log

```
mkdir -p data/db/log
cd data/db/log
touch mongod.log
```

在etc文件夹下创建文件mongodb.conf

```
cd /etc
vmi mongodb.conf
//开始编辑  i
// 文件内容
dbpath=/usr/local/mongodb4/data/db
logpath=/usr/local/mongodb4/data/db/log/mongod.log
logappend=true
fork=true
// 表示任意源地址都可以访问mongodb服务
bind_ip=0.0.0.0 
port=27015
// 退出编辑 esc
// 保存 ：wq

再次启动mongodb mongod -f /etc/mongodb.conf
```

