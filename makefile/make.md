# Makefile

## Makefile文件中通常包含如下内容
- 需要创建的target，通常是目标文件或可执行文件
- 依赖文件
- 创建每个target时，需要运行的命令

## 运行Makefile
输入make命令后，会在当前目录下搜索文件名"makefile" "Makefile"。  
当然你也可以使用别的文件名，比如ubuntu_makefile，此时就要用-f 或--file指定该文件。  
make -f ubuntu_makefile

## makefile包含5部分内容
- 显式规则
- 隐式规则
- 变量定义
- 文件引用
- 注释

## 什么是目标文件？
目标文件就是源代码在汇编之后、链接之前生成的那些中间文件，Linux下的.o文件就是目标文件。目标文件和可执行文件内容与格式几乎一样，都是按照ELF文件格式存储的，所以我们可以广义的将目标文件和可执行文件看成一类。

## 变量
$@ target文件
$+ 依赖项