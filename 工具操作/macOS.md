





打开并编辑macOS环境变量配置.zshrc

```
open .zshrc
```

修改配置文件.zshrc并保存使之生效

```
source .zprofile
```







安装多版本python

```
brew install pyenv
```

如果遇到错误提示部分依赖包无法下载，则单独对依赖包使用brew install 安装即可

```
pyenv -v //查看pyenv版本
```

pyenv 在macOS 上存在兼容问题待修复，解决方法折腾，

安装conda  https://blog.csdn.net/jhyfugug/article/details/125024458

下载地址 https://gitcode.net/mirrors/conda-forge/miniforge?utm_source=csdn_github_accelerator

执行下载后的sh文件

安装完成后

conda env list 显示所有虚拟环境

conda create --name python_env 创建虚拟环境

conda create --name venv python=3.7 numpy pandas 指定Python版本创建虚拟环境并安装指定依赖项









macOS 切换brew镜像源，解决安装某些包问题

https://www.jianshu.com/p/50c2eeb68da9



burp安装

https://blog.csdn.net/qq_40810532/article/details/123692311



nvm 

设置默认node版本

nvm alias default v16.14.0



Sdkman 管理jdk grade

```
sdk install gradle 5.6.4
```
