---
layout:     post
title:      String
subtitle:   String及其实现
date:       2024-09-18
author:     Suzuhiki
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - stl
---

# 前言
因为学了String的相关内容,于是打算在这里更新学习过程中的一些体会

# 正文
String是C++的一个类,用来表示字符序列(怎么感觉这是废话)

# String的构造
根据C++标准库,可以看到String的构造方法

```
#常见的构造方法
string();

#拷贝构造,使用引用在一般情况下可以使效率更高,但是使用引用,如果在函数中修改了参数的值,那么这个变量本身也会被修改
#为了防止这个变量被修改,使用const来修饰,防止其被修改
string (const string& str);

#加了两个size_t参数用来表示这个拷贝构造从str[pos]开始拷贝到结束,npos为size_t的-1
#实际上,不写后面的那个参数,也会默认拷贝到结束,比如这个
string (const char* s, size_t n);
#使用了迭代器来构造
template <class InputIterator>
string  (InputIterator first, InputIterator last);

```

# 写点String的函数的用法
`size` 用来返回字符串长度
`max_size` 这个返回字符串最大长度,这个最大长度往往和操作系统以及编译器有关
`resize` 顾名思义,重新调整rize的大小
用法在这
```
#include<string>
#include<iostream>
using namespace std;
int main()
{
	string s1 = "suzuhiki";
	s1.resize(s1.size() + 2);
	cout << s1.size() << endl;
	cout << s1 << endl;
	s1.resize(s1.size() + 2,'a');
	cout << s1.size() << endl;
	cout << s1 << endl;
	s1.resize(7);
	cout << s1.size() << endl;
	cout << s1 << endl;
	return 0;
}
```
输出结果:
10
suzuhiki
12
suzuhikiaa
7
suzuhik

扩容却不添加字符就会只扩大size而不改变别的,而如果resize比原来小就会删掉多余的字符
```
#include<string>

int main()
{
    string s1 = "suzuhiki";

    return 0;
}

