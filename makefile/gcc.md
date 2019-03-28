# GCC(GNU Compiler Collection)
## gcc与g++的区别
- gcc调用GCC中的GNU C Compiler
- g++调用GCC中的GNU C++ Compiler
- 对于.c和.cpp文件，gcc分别当做C和C++编译
- 对于.c和.cpp文件，g++统一当做cpp文件编译
- 使用g++编译时，g++会自动链接标准库STL，而gcc不会自动链接STL

## GCC编译流程
预处理(preprocessing)之后，生成.i文件  
编译(compiler)之后，生成.s文件  
汇编(assembly)之后，生成.o文件  
链接(linking)之后，生成可执行文件

## GCC常用选项汇总
选项|含义
----|-----
-E|生成.i文件
-S|生成.s文件，即汇编代码
-c|生成.o文件
[infile] -o [outfile]|infile outfile可以是一个文件，也可以是一组文件。
-I(i的大写)|指定头文件路径
-L|指定动态库或静态库的路径
-l(L的小写)|紧挨着的就是库名name
-g|生成能被gdb使用的调试信息

- 注意：gcc编译选项会区分大小写。因此-o 和 -O是不一样的。前者表示生成可执行文件，不用-o的话会默认在当前文件夹下生成a.out。后者表示生成可执行文件并且进行一级优化。

## 链接其它目录中的库

```shell
//要添加的数学库是libm.so，其中库文件名是libm.so，库名是m
//GCC会在库名基础上，自动添加前缀lib和动态库后缀.so或者静态库后缀.a
gcc main.c -o main.out -lm`  
```
  
比如，我们用到第三库的库文件名叫libtest.so，那么我们只需要把libtest.so拷贝到/usr/lib里，编译时加上参数-ltest，我们就能用上libtest.so了（当然还需要libtest.so配套的头文件）。

Q1：-l(L的小写)链接的到底是动态库还是静态库?  
Ans：如果链接路径下同时有.so和.a，会优先链接动态库。

Q2：如果路径下同时有静态库和动态库，如何链接静态库?  
Ans：显示的指明静态库的名字, `gcc -l:libxxx.a`  

标准库一般位于/lib/ 或 /usr/lib/ 或 /usr/local/lib。GCC会在标准库目录中搜索库文件。如果想链接的库没放在这3个目录里，就得特别指明。有3种方式可以链接到GCC搜索路径以外的链接库。

1. 为GCC指定该链接库的完整路径与文件名
例如，若链接库名为libm.a，并且位于/usr/lib目录  
`gcc main -o main.out /usr/lib/libm.a`

2. 用-L选项，为GCC增加一个搜索链接库的目录  
`gcc main -o main.out -L/usr/lib -lm`  
可以使用多个-L选项，或者一个-L选项内使用冒号分割的路径列表。

3. 把所需链接库的目录添加到环境变量LIBRARY_PATH 或 LD_LIBRARY_PATH中。

环境变量|描述
----|-----
LIBRARY_PATH|加载运行的时候搜索库目录
LD_LIBRARY_PATH|编译的时候搜索库目录

添加LIBDIR1 LIBDIR2库目录
`export LIBRARY_PATH = LIBDIR1:LIBDIR2:$LIBRARY_PATH`

## 为什么会出现undefined reference to 'xxxx'错误？
首先这是链接错误，不是编译错误。如果只有这个错误，说明你的源码没问题，是编译时用的参数不对，没指定要用到的库。比如，程序中用到了一些数学函数，那么就要在编译命令中加入-lm