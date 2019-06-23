---
title: 关于c++的可调用的函数对象
date: 2018-10-15 14:31:29
tags: [记录, c++11, codewars]
---

关于函数的对象调用，可以是函数指针、lambda表达式、重载的某类对象。

```c++
int f_add(int i,int j){return i+j;}
```

该函数为普通函数，可以通过函数指针来进行调用。

```c++
int(*f)(int, int);
f=f_add;
cout << f(3, 4) << endl;
```

```c++
auto l_add = [](int i,int j){return i+j;};
```

 <!--more--> 

该函数为lambda表达式，



```c++
class c_add{
public:
    c_add()=default;
    int operator()(int i,int j){return i+j;}
};
```

该函数为重载()，可以使用如下方式调用

```c++
auto f3 = c_add();
f3(3,4);
```

