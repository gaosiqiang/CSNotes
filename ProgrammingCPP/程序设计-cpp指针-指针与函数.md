# 指针与函数

## 1、指针做函数参数
在函数的调用链中可以将指针类型变量当做函数的实参传递过去；

```cpp
void Rank(int *p1, int *p2)  
{  
    int temp;  
    if (*p1 > *p2) {  
        temp = *p1;  
        *p1 = *p2;  
        *p2 = temp;  
    }  
    return;  
}  
  
int main()  
{  
    int a = 2, b = 1;  
    int *p1 = NULL, *p2 = NULL;  
    p1 = &a, p2 = &b;  
    Rank(p1, p2);  
    cout << a << endl; // 1  
    cout << b << endl; // 2  
    return 0;  
}
```

代码分析：
主函数main中定义了变量a和b和指针p1和p2，然后将p1和p2做为参数传递给函数Rank，转递的值分别是指向变量a和b的指针，在函数Rank中开辟了新的内存栈区中创建了指针p1和p2和变量temp，这些变量与main主函数的变量之间在不同的内存栈区都是局部变量不会互相影响。

但是函数Rank可以通过指针p1和p2访问读写main函数栈区的变量a和b。


## 2、数组名做参数（实参）
在函数的调用链中可以将函数名当做函数的实参传递过去，实际上是将数组的第一个元素的指针变量当做实参传递过去的；

```cpp
int sumArray(int *p, int n)  
{  
    int total = 0;  
    for (int i = 0; i < n; i++) {  
        total += *p++;  
    }  
    return total;  
}  
  
int main()  
{  
    int a[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};  
    int n = 10;  
    cout << sumArray(a, n) << endl; //55  
    return 0;  
}
```

代码分析：
1、主函数中的数组a的名是指向第一个元素的指针；

2、在sumArray函数中通过指针遍历数组a的全部元素运算得出结论；


## 3、函数名做形参
函数形参中定义一个数组就相当于定义了这个数组名的指针变量；编译器将函数的形参数组名作为指针变量处理；

函数定义中的，int \*p 与 int p[]是等价的；

```cpp
void testFunction(int a[])  
{  
    cout << a << endl;  
    cout << *(a + 1) << endl;  
    return;}  
  
int main()  
{  
    int a[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};  
    cout << a << endl;  
    testFunction(a);  
    return 0;  
}
```

代码分析：
main函数与testFunction函数输出的地址一致，验证了上面的说法；

## 4、指向符号常量的指针
> 限制函数中使用指针的权限，只给函数的读取的权限不给写入的权限；

> 限制函数使用指针的权限的方式可以将函数的形参的指针用const修饰符定义成指向符号常量的指针；

定义语句：`const int *p;`；就是定义指向符号常量类型的指针；所以无法通过指针对其指向的内容进行修改，但是指针变量可以修改；

函数中的应用：

```cpp
void testFunction(const int *p)
{
	*p = 1;//非法代码
	p += 1;//合法代码
	return;
}
```

指针p指向的内容是字符常量；实现了对指针的权限控制，保护了指针所指向的内容的安全性；

特性：
1、指针p指向的内容不能被修改，只能被读取；

2、指针p存储的指针是可以被修改的，`p += 1;`是可以的，指针变量p可以被修改，但是p所指向的内容不能；


## 5、返回指针值的函数
指针作为函数的返回值；

### 5.1、定义规范
数据类型 \*函数名(参数列表){
    函数体;
}

### 5.2、声明定义

```cpp
int *testFunction(params);
```

这里声明定义了返回值int基类型的函数；

1、int是返回指针的基类型；
2、\*是指针运算符；
3、testFunction是函数名；

### demo1

```cpp
int *getPtr(int a[][5], int n, int m)  
{  
    int *ptr = NULL;  
    if (n > 0) {  
        n -= 1;  
    }  
    if (m > 0) {  
        m -= 1;  
    }  
    ptr = *(a + n) + m;  
    return ptr; //return(ptr);
}  
  
int main()  
{  
    int a[3][5] = {  
            {1, 2, 3, 4, 5},  
            {6, 7, 8, 9, 10},  
            {11, 12, 13, 14, 15}  
    };  
    cout << *getPtr(a, 1, 5) << endl; //5
    return 0;  
}
```

代码分析：
1、int \*getPtr(int a[][], int n, int m)是声明定义了返回值以int为基类的指针类型；

2、int a[][5]是定义形参数组，a会被当成指针变量处理。注意一点的是：'a'声明为多维数组除第一个维度外的必须对所有维度都要有边界。也就是为什么第一维度可以不用定义边界；

3、返回语句return ptr;可以用return(ptr);return函数返回的方式；

### demo2

```cpp
int *getPtr()  
{  
    int a = 20;  
    return &a;  
}  
  
int main()  
{  
    int *p = NULL;  
    p = getPtr();  
    cout << *p << endl;  
    return 0;  
}
```

这个代码在编译过程中会报错：warning: address of local variable 'a' returned [-Wreturn-local-addr]

代码分析：
1、先执行main函数；
2、执行到调用函数getPtr，在内存中开辟出新的栈区；
3、执行函数getPtr函数，函数中定义了局部变量a；
4、函数getPtr返回局部变量a的内存地址；
5、回收调用getPtr函数开辟的内存栈区；
6、main函数通过getPtr返回的地址，访问内容；

错误分析：
函数getPtr在被回收后所在的内存空间被释放了，原来局部变量a的内存空间内容是不确定的，所以依据指针获取到的内容是未知的；

原则：
1、所以函数要返回一个处于生命周期中的变量地址；
2、返回全局变量的指针，而非局部变量的指针；
3、返回静态局部变量的指针，而非动态局部变量的指针；

## 6、静态局部变量

### 概念
静态局部变量：函数中的局部变量的值在函数调用结束后仍然保持原来的值；

### 定义规范
用关键字static进行声明；
`static 数据类型 变量名;`

### 声明定义

```cpp
static int a = 10;
```

定义了静态变量；

### 应用

```cpp
void function_name()
{
	static int a = 10;
}
```

定义了局部静态变量；

### demo

```cpp
int *test()  
{  
    static int a = 20;  
    return &a;  
}  
  
int main()  
{  
    int *p = NULL;  
    p = test();  
    cout << *p << endl; //20  
    return 0;  
}
```

代码分析：
test函数中的a是静态局部变量是不会随着test函数内存空间的释放而释放的；

### 拓展

1、以前的c/cpp版本中，定义局部动态变量的规范是 `auto int a = 10;` 现在这个auto是可以省略不写的，编译器默认自动加上；

2、在c++2011标准规范中，auto与之前版权的auto的含义有本质上的不同；