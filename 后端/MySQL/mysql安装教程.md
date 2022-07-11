# MySQL安装教程

## 一、下载

​	官网下载想要的版本的mysql压缩包，若遇到下载太慢，在浏览器下载任务队列中右击复制下载链接到迅雷中下载。

## 二、本地配置

	-  解压缩文件到MySQL要安装的目录，**目录中不要有中文**；
	-  将文件的bin路径添加到系统环境变量的PATH中；
	-  在bin同级目录创建data文件夹；
	-  在bin目录下新建my.ini文件；
	-  在my.ini文件中编辑如下；

```
[client]
port = 3306
 
[mysqld]
#设置3306端口
port = 3306
# 设置mysql的安装目录 tips:这里的目录是你自己的安装目录，这个是我的安装目录，你不能用的哦
basedir=E:\software\MySQL\mysql-8.0.27
# 设置mysql数据库的数据的存放目录 tips:同上一条
datadir=E:\software\MySQL\mysql-8.0.27\data
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
#这个需要注意一下，不然报错
#其原因是从 5.6开始，timestamp 的默认行为已经是 deprecated 了。
explicit_defaults_for_timestamp=true
 
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
```

## 三、初始化数据库

- 以管理员权限打开cmd,进入到MySQL安装目录下的bin文件夹，输入命令

  ```
  mysqld --initialize --user=mysql --console
  ```

  初始化会产生一个临时密码把这个临时密码复制下来

  <img src="F:\GithubCode\studyNotes\assets\img\后端\MySQL\20220414223924.png" style="zoom:200%;" />

- 输入安装命令：

  ```
  mysqld --install  mysql
  ```

- 使用临时密码进入数据库

  ```
  mysql -uroot  -p
  ```

  如果报错则可能mysql服务未启动，启动服务命令

  ```
  net start mysql
  ```

- 进入数据库后修改临时密码为自己的密码

  ```
  set password='yourpassword';
  ```

  

关于Navicat 的安装与破解：http://www.downcc.com/soft/430673.html