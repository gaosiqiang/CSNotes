# 程序设计-指针变量

## 3、指针变量

### 3.1、概念定义
1、指针变量：专门用于存储指针（某个资源的内存地址）的变量叫做**指针变量**；但是很多时候就只叫做**指针**；

### 3.2、特点
1、指针变量属于指针数据类型，就是存储指针类型的变量数据类型；，也是变量也遵循变量三要素：名称、资源、指针地址。也就是指针变量自己也有一个属于自己存储空间的指针与普通变量没有什么区别；

2、因为指针变量存储的资源是指针，表述的时候可以称为为：**指向‘资源名’的指针变量**。

3、如果一个变量a的地址也就是指针是另一个指针变量p存储的值，那么这个**p就是指向变量a的指针变量**；

### 3.3、指针变量与其他变量的区别
指针变量只能存储指针类型数据，而普通类型是可以存储除指针类型其他的类型数据；

### 3.4、声明定义指针变量
#### 3.4.1、指针类型的变量声明定义规范
通过指针运算符\*标示了变量为指针变量类型变量，这样就定义了指针类型的变量来存储‘指针’资源；

```cpp
基类型 *变量名;
baseTypeName *pointerVariableName;//定义指针变量
```

> 基类型，用来指定指针变量的基类型。基类型是指针变量所指向变量的数据类型；

> 基类型可以理解为指针变量存储的指针，所指向的资源数据类型，都是c/cpp中基础的常用的类型；

> 这个基类型，称作指针变量的基类型；

#### 3.4.2、声明定义demo：

```cpp
#include <iostream>
using namespace std;

int main()
{
    int *pointer;//定义了一个指针变量。
    return 0;
}
```

指针变量声明定义规范demo代码解析：

- int是基类型，可以把int称作指针变量pointer的基类型。
- *是标识了变量为指针类型
- pointer是指针变量名称


### 3.5、指针变量的使用
#### 3.5.1、指针变量赋值规范
将获取到的变量的指针赋值给指针变量即可。

```cpp
baseTypeName *pointerVariableName;//定义指针变量
pointerVariableName = &variableName;//指针变量的赋值
```

赋值完成后，称为指针变量pointerVariableName指向了变量variableName，也称为pointerVariableName指针指向variableName；

因为pointerVariableName是指针类型变量，所以直接使用`pointerVariableName = variableName;`变量赋的值不是指针类型数据那么赋值运算是非法代码，指针变量只能接受指针类型数据同时符合基类型的指针才能赋值；

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

#### 3.5.2、指针变量访问所指向的变量的规范
指针变量访问存储的指针对应的资源：因为指针变量存储的就只是指针而已，打印出来就可以看到就只是指针而已。可以用指针运算符\*实现访问指针对应的资源；简而言之：通过指针访问资源；

```c++
baseTypeName variableName;//定义基础变量
baseTypeName *pointerVariableName;//定义指针变量
pointerVariableName = &variableName;//指针变量的赋值
cout << *pointerVariableName << endl;//通过*加上指针变量名。可以访问指针变量pointerVariableName存储的指针所指向的variableName变量的资源。
```

\*pointerVariableName就是访问pointerVariableName指针变量内存储的指针所指向的存储单元的内容。这个内容是variableName变量而不是指针变量pointerVariableName存储的指针对应的内存资源；所以\*pointerVariableName可以当做variableName来使用；

##  指针与指针变量的区别和联系
1、经常将指针变量就直接称作指针；但是指针与之指针变量在概念上是有所区别的；

2、这里表述的是**指针**，而不是**指针变量**，这两个是不同概念。指针变量是存放内存地址的变量，而且指针变量有自己的数据类型也就是指针类型；

3、也就是说指针本质上是值，是变量在内存中的地址；指针变量是存放指针这个值的变量；