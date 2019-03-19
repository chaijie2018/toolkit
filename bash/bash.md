## Xshell快捷键
```shell 
// 上传本地文件至服务器(前提是已安装lrzsz)
 rz
 // 弹出连接会话窗口
 alt + o
 // 密码
 chaijie 密码 fff
 root 密码 FFF
 ```
 
 ## 软件包管理（以cmake为例）

 ```shell
 // 搜索软件包
 yum search cmake
 // 列出已有的软件包
 yum list | grep cmake
 // 列出本地已安装的软件包
 yum list installed | grep cmake
 // 删除软件包
 yum erase cmake
 // 可更新的软件包列表
 yum list updates
 // 升级cmake
 yum update cmake
 // 列出cmake信息
 yum info cmake
 ```
 
## 查看当前目录下所有文件大小
```shell 
// 查看目录e200_opensource下所有文件大小
// -d 最大深度
du -d 0 -h e200_opensource/
du -d 1 -h e200_opensource/
```

## 对命令 `/dev/null 2>&1`的解释

```shell
cat dhuddd >/dev/null 2>&1
```
1. 数字含义

名称|代码
-----|----
标准输入(stdin) | 0
标准输出(stdout) | 1
标准错误输出(stderr) | 2

2. /dev/null 表示空设备。  
它是一个特殊的文件，写入它的内容会被全部丢弃。但/dev/null非常有用，会起到“禁止输出”的效果。  
因为系统默认值是1，所以`>/dev/null` 等同于 `1>/dev/null`

3. `2>&1`含义：将标准错误输出重定向到标准输出  
符号>&是一个整体，不可分开，分开后就不是上述含义了。 比如有些人  
可能会这么想：2是标准错误输入，1是标准输出，>是重定向符号，那么  
"将标准错误输出重定向到标准输出"是不是就应该写成”2>1”就行了？是这样吗？  
如果是尝试过，你就知道2>1的写法其实是将标准错误输出重定向到名为”1”的文件里去了.
