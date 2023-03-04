# vscode使用手册

[TOC]



## 1.插件的使用

### 1.1koroFileHeader(注释模板)插件

```
    //settings.json
    
    "fileheader.customMade": { //文件头部注释 ctrl+alt+i
        "Author":"yanggl",
        "Date":"Do not edit",
        "LastEditTime":"Do not Edit",
        "Descripttion":"",
        "autoAdd":false //是否自动添加注释
    },
    "fileheader.cursorMode": { //函数注释 ctrl+alt+t
        "Descripttion":"",
        "params":"",
        "return":"",  
    },
```

### 1.2GitHub Repositories

该插件可以在vscode预览GitHub源代码库

## 2.常见问题

###  2.1新版vscode启动一段时间后界面显示模糊

在桌面的vscode启动快捷方式右键打开属性，做如下配置：在启动命令后面添加  `--disable-gpu`  禁用gpu加速，重启vscode。

<img src="https://github.com/Youngygl/studyNotes/blob/master/assets/img/20200609004650.png" style="zoom: 67%;" />

### 2.2 vscode每次只能打开一个文件不会新增tab页

在settings.json添加如下设置：

```
"workbench.editor.enablePreview": false
```

