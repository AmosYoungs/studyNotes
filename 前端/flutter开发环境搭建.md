

### 下载与安装

参考官网下载flutter包，配置相关环境变量

执行`flutter doctor` 检查flutter是否所需环境都安装好

一些依赖的解释与安装：

### CocoaPods 

在进行 iOS 开发时免不了会使用第三方的开源库,使用这些开源库通常需要:

- 下载开源库源代码并 引入工程
- 想工程中添加开源库使用到的 framework
- 解决 开源库和工程 ,开源库和开源库之间的依赖关系,检查重复添加的 framework 等问题
- 如果开源库有更新的时候,还需要 将工程中的开源库更新到最新的版本

CocoaPods是一个ruby包，所以需要 rvm，gem来管理

- [rvm](https://link.zhihu.com/?target=https%3A//rvm.io/)：ruby 版本管理工具，可以设置当前版本/安装/卸载
- [gem](https://link.zhihu.com/?target=https%3A//rubygems.org/): 全称 RubyGems，是 ruby 的软件包管理工具
- [brew](https://link.zhihu.com/?target=https%3A//brew.sh/): 全称 Homebrew，macos 的软件包管理工具

安装rvm

下载

```shell
curl -L get.rvm.io | bash -s stable
```

指定源

```shell
source /Users/amosyoung/.rvm/scripts/rvm
```

查看是否安装成功

```shell
rvm -v
```

列出所有版本

```shell
rvm list known
```