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

```

