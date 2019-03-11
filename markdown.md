# Demo1

## 段落

句子末尾加两个空格会分段，间隔空行也会自动分段。  
我是柴杰，我喜欢开源ISA CPU，很喜欢开源社区的技术和氛围。
现在我的研究方向是存算融合架构设计。

## 强调

**粗体**  *斜体*  ***加粗倾斜***
~~我是删除线~~

## 列表

### 无序列表
My profile
- Name: chaijie
- Email: chaijie@mail.ustc.edu.cn

### 有序列表
My profile
1. Name : chaijie   
2. Email : chaijie@mail.ustc.edu.cn
 
## 链接

### 内嵌式链接

- 外部链接: [百度](http://www.baidu.com)
- 链接至仓库其它文件）: [markdown_list](markdown_list.md)
- 链接至本文档其它部分: [代码块](markdown.md#代码块)

### 引用式链接
避免长链接的视觉扰乱，让文档可读性好。  
[百度]  
[markdown_list]  
[代码块]

## 图片

语法格式：![text](url "message")  
说明：
- text: 图片显示不了就显示文字，可以缺省
- message: 鼠标移动到图片处显示的文字，可以缺省
- url: 不可缺省, 相对/绝对地址均可
![](https://www.baidu.com/img/bd_logo1.png?where=super "百度Logo")
![](相对路径)

图片引用式链接
![][baidu_logo]
![][newlife]
## 引用

> 这是一个引文。

——出自《出处》

## 代码块
- 行内代码
这个代码中用来声明变量是`var a = 10`,打印变量内容是`console.log`函数的调用。

- 块状代码
```javascript
var a = 10;
console.log(a);
```
## 水平分割线(前面必须留有空行)

---
Horizontal Rule

---
## 表格
|    这|    是 |    表|    头|
|------|:------:|------:|------|
|cell  | cell2|cell3  |[百度]|
|**row 1** |row 2 | cell 3| ![][baidu_logo]|


精简表格
    这|    是 |    表|    头
------|:------:|------:|------
cell  | cell2|cell3  |cell4 
row 1 |row 2 | cell 3| row 4

## GFM
Git Flavored Markdown

## HTML 代码
<p align='center'> Hello World!</p>

<!--我是行注释-->
<!--
我是块注释
-->
[百度]: http://www.baidu.com
[markdown_list]: list.md
[代码块]: demo1.md#代码块

[baidu_logo]: https://www.baidu.com/img/bd_logo1.png?where=super
[newlife]: newlife.jpg
