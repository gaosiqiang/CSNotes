# 指针

## 1、导读

指针学习目标：指针在c语言中占有很重要的地位。从概念上就打好指针方面的基础。关于指针的学习概念是很重要的部分，所以要理解性的学习指针方面的知识。

## 2、指针

### 2.1、指针概念定义
指向一个内存资源的**内存地址**即为**指向该资源的指针**，而内存地址即为**指针**。

通常把某个变量的内存地址称为指向该变量的指针。一个变量的地址就是指向这个变量的指针。

### 2.2、指针的意义
通过指针访问指针指向的标定资源。

> PS:这里表述的是**指针**，而不是**指针变量**，这两个是不同概念。

### 2.3、指针的使用

#### 获取指针
获取方式：通过指针运算符&来获取指针

获取指针表达式：

```cpp
&加上资源名称; //即可获取该名称资源的指针。也就是资源内存存储区域的起始单元的内存地址。
```

example1

```cpp
int a = 1;
&a; //获取变量a内存存储地址，即为获取指向变量a的指针。
int b;
cout << &a; //打印出变量a的指针。
```

example2

```cpp
#include <iostream>
#include <typeinfo> //引入typeinfo类库
using namespace std;

int main()
{
    int a = 100;
    cout << &a << endl; //输出变量a的指针
    cout << typeid(a).name() << endl; //输出i表示是int类型
    cout << typeid(&a).name() << endl; //输出Pi表示类型是指针，指向整数int资源的指针

    char b;
    b = 'a';
    cout << &b << endl; //输出变量b的指针
    cout << typeid(b).name() << endl; //输出c表示是char类型
    cout << typeid(&b).name() << endl; // 输出Pc表示类型是指针，指向字符char资源的指针

    cout << sizeof(&a) << endl; //输出该指针在内存中的存储多个个字节空间
    cout << sizeof(&b) << endl; //输出该指针在内存中的存储多个个字节空间

    return 0;
}
```


指针的大小可以用sizeof函数获取，同样的代码在不同的编译器中指针的大小是不同的。比如docker的centos是8个字节。

#### 通过指针获取资源
指针运算符&加上资源名只是获取资源的指针，比如`&a;`只是获取a的指针。而获取指针对应的资源就需用另一个：指针运算符*

表达式格式：

```cpp
*加上指针;
```

example：

```cpp
#include <iostream>
using namespace std;

int main()
{
    int a = 100;
    cout << a << endl; //打印a的值，输出100
    cout << &a << endl; //打印a的指针，输出0x7fff8c685fa8，不同的环境可能不同
    int b;
    b = *&a; //将a指针指向的资源赋给b
    cout << b << endl; //打印b的值，输出100
    cout << *&a << endl; //打印a指针指向的资源，输出100
    return 0;
}
```


### 2.4、小结

`*&c`和`c`在c/cpp代码中是等价的。就是使用指针运算符\*加上指针访问资源和直接在代码中使用资源名访问资源这两种方式是等价的。

用指针运算符\*就可以去访问这个指针指向的资源。对于这个变量c的指针，我们又可以用\*加上这个地址，去访问这个资源。如果想用这个地址访问a的值并且打印 `cout<<*&a`。

编译时，编译器建立 变量名 到 地址 的映射。

## 3、指针变量

指针变量：专门用于存储指针（某个资源的内存地址）的变量叫做**指针变量**。

指针变量与普通变量只有存储的资源不同而已，因为指针变量存储的内存资源是指针地址，其他没有什么不同。指针变量也要有三要素：名称，资源，指针地址，也就是指针变量自己也有一个属于自己存储空间的指针与普通变量没有什么区别。

因为指针变量存储的资源是指针，表述的时候可以表述为：**指向‘资源名’的指针变量**。本来是2个变量因为指针变量存储了另一个资源的指针所以两个资源名称就有了关系。

**指针变量属于一种数据类型，就是属于指针数据类型。**

重点要理解指针与指针变量的区别：
1、什么是指针，内存地址
2、什么是指针变量，存储指针类型的变量数据类型
3、什么是指向资源名的指针变量，是表述方式

### 3.1、声明定义指针变量
指针类型的变量声明定义规范：定义一个指针类型的变量来存储‘指针’资源。

```cpp
基类型 *变量名;
baseTypeName *pointerVariableName;//定义指针变量
```

基类型，用来指定指针变量的基类型。基类型是指针变量所指向变量的数据类型。可以理解为指针变量存储的指针所指向的资源数据类型，都是c/cpp中基础的常用的类型。

\*变量的类型，这里的\*是指针运算符，在这里标示了变量为指针变量类型变量。

```cpp
#include <iostream>
using namespace std;

int main()
{
    int *pointer;//定义了一个指针变量。
    return 0;
}
```

指针变量的定义规范解析：

	int是基类型，可以把int称作指针变量pointer的基类型。
	*是标识了变量为指针类型
	pointer是指针变量名称


### 3.2、指针变量的使用
指针变量赋值规范：将获取到的变量的指针赋值给指针变量即可。

```cpp
baseTypeName *pointerVariableName;//定义指针变量
pointerVariableName = &variableName;//指针变量的赋值
```

赋值完成后，称为指针变量pointerVariableName指向了变量variableName。

因为pointerVariableName是指针类型变量，所以直接使用`pointerVariableName = variableName;`变量赋值不是变量的指针赋值是非法代码，指针变量只能接受指针类型数据同时符合基类型的指针才能赋值。

example：

```cpp
#include <iostream>
using namespace std;

int main()
{
    int *pointer; //定义了一个指针变量。
    int a = 100;
    pointer = &a; //&a获取a的指针，然后赋给指针变量pointer。赋值后，称指针变量pointer指向了变量a。
	cout << pointer << endl; //输出的是指针地址
    return 0;
}
```

指针变量访问存储的指针对应的资源：
因为指针变量存储的就只是指针而已，打印出来就可以看到就只是指针而已。可以用指针运算符\*实现获取指针对应的资源。

```c++
baseTypeName *pointerVariableName;//定义指针变量
pointerVariableName = &variableName;//指针变量的赋值
cout << *pointerVariableName << endl;//通过*加上指针变量名。可以访问指针变量pointerVariableName存储的指针所指向的variableName变量的资源。
```
\*pointerVariableName就是pointerVariableName所指向的存储单元的内容。

所以`*&variableName`和`variableName`在c/cpp代码中是等价的。


## 引用参考

## 总结

## 拓展

连接：https://apod.nasa.gov/apod/image/0403/n49_hst_full.jpg
名称：N49星云
图片：![](./images/n49_hst_full.jpeg)


通过连接就可以获取到名字叫N49星云的图片资源。连接就是这是图片的地址。图片就是连接对应的对应的资源，名称就是该资源的名称。

可以把连接称为指向这个资源的指针（这里资源这里是指图片）。

这个连接就把它称作指针。
