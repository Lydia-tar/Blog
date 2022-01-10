# 认识数据结构与算法

## Chapter 1 准备工作

为了记录用C学习数据结构与算法，因为基础有限，就学到什么记录什么吧。记录结构使用：why--what--how （why 就是为什么要有这项技术，这项技术目的是啥，what是这个技术是什么，how就是怎么实现的）

### 写c的ide选择 codeblocks

> why

 1. 因为这个比较轻量，自带编译器二进制版本,不需要配置环境，直接使用。visual studio比较臃肿.codeblock 的安装使用方面要比visual studio 方便很多，codeblock只需要创建个文件，保存后就可以直接编译执行，而visual studio需要创建一个项目。

 2. 跨平台使用：不管是在Windows还是Linux下都可以使用

> what

一种IDE(集成开发环境)

>how

这次安装时间在10min之内。 [下载安装](https://cloud.tencent.com/developer/article/1708117)


### C 指针与数组

指针

> why


1. 在某些情况下指针是表示计算的唯一方法

2. 使用指针编写代码通常比用其他方法更加简洁高效


> what


1. 一个对象由两部分组成，对象的内容+对象在计算机中的存储位置。指针的作用就是可以通过*，&来读取对象的内容和地址。

> how 

1. &：读取对象地址。 `p = &c` 即将c的地址赋值给变量p.

   *:读取对象内容。`y = *p` 即y读取了指针p指向的c的内容。

数组

> why

> what

> how 