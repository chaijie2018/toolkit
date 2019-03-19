# Linux Shell脚本编程入门

## 指定脚本解释器

```shell
// 指定用/bin/bash编译解释，必须第一行顶格写
#!/bin/bash
```

## 直接赋值和间接赋值

```shell
// 用户变量要小写，要养成好习惯
// 变量直接赋值
a=10
echo $a
// 释放变量
unset a
echo $a
// 变量间接赋值
read -p "Give me a number:" a
666
echo $a
```

## 两个常用的内置变量 $PATH $UID
```shell
// 系统变量是大写
// 中括号表示判断，当前用户的uid不等于0
// root的 uid 为0
[$UID -ne 0]

// 上一条命令执行成功则为0，执行失败为非0
echo $?
```

## 在屏幕上打印内容

```shell
// 打印菜单，中间是内容，最后的EOF必须顶格写
cat << EOF
这里写要显示的内容
EOF
```

## 比较数字和字符串

```shell
// 比较用[  ]，注意前后有空格，< > = !=
// && 条件为真执行，|| 条件为假执行
[ 2 = 3 ] && echo 0 || echo 1

// 如果config.v大于10行，就打开该文件
line=`cat config.v | wc -l`
[ line > 10 ] && cat config.v

var=chaijie
[ var = chaijie ] && echo 0 || echo 1
```

## 中括号中的其它判断

```shell
// string为空值，就打印0
[ -z $string ] && echo 0
// string不是空值，就打印0
[ ！-z $string ] && echo 0
// 比如，若dir是空值，会把/root删掉
dir=tmp
rm -rf /root/${dir}

// file文件存在，则为真
[ -f $file ]

// file有执行权限
// 文件名为绿色表示有执行权限
[ -x $file ]

// 如果目录directory存在，则为真
[ -d $directory]
```

##  调用函数

```shell
// 函数要先定义再调用，调用时用函数名（不必加小括号）
// 函数内外变量没有局部和全局之分，不需要传参
error_info(){
	echo "This directory does not exist."
	echo This directory does not exist\.
	echo "..."
	echo \.\.\.
}

dir=/root/bin
[ ! -d $dir ] && error_info
```