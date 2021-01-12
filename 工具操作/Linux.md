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

下载安装mysql

cd /usr/local/download

wget https://cdn.mysql.com/archives/mysql-5.7/mysql-5.7.30-linux-glibc2.12-x86_64.tar.gz

tar -zxvf mysql-5.7.30-linux-glibc2.12-x86_64.tar.gz

复制移动重命名  cp -r  mysql-5.7.30-linux-glibc2.12-x86_64  /usr/local/mysql

```
创建mysql用户组和mysql用户
groupadd mysql
useradd -r -g mysql mysql
groups mysql
修改mysql目录拥有者为刚建立的mysql用户
cd mysql/
chown -R mysql:mysql ./
```

```
初始化配置：
bin/mysqld --initialize --user=mysql --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data
```

上面命令执行报错：安装以下文件

```csharp
yum install  libaio-devel.x86_64
```

重复初始化配置：若还报错安装执行以下命令

```csharp
yum -y install numactl
```

```
 修改mysql目录拥有者为root用户，修改data目录拥有者为mysql
 chown -R root:root ./ && chown -R mysql:mysql data
```

设置SSL安全连接mysql（RSA加密），指定mysql目录和data目录

 bin/mysql_ssl_rsa_setup --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data

 bin/mysqld_safe --user=mysql --basedir=/usr/local/mysql/ --datadir=/usr/local/mysql/data &

```
将mysql加入/etc/init.d启动引导：
cp support-files/mysql.server /etc/init.d/mysql
```

qDe6wqtGvs#y

**Linux 添加环境变量**

- vim ~/.bashrc   //进入环境变量配置文件
- 加入要写的配置

- source ~/.bashrc   //配置永久生效