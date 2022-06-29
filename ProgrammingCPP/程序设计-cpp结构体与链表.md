# 结构体与链表

## 结构体
概念：是一次定义一组变量的自定义数据格式

### 结构体类型与结构体变量
结构体变量也可以称作结构体类型变量；

#### 定义规范
struct 结构体名 {
	数据类型 变量名1;
	数据类型 变量名2;
	数据类型 变量名3;......
};

#### 声明定义

```cpp
struct struct_name{
	int id;
	char name[25];
};
```

#### 创建
定义结构体类型变量，和子变量，并初始化；

```cpp
struct_name p = {
	123,
	{'n', 'a', 'm', 'e'}
};
```

也可以选择定义结构体类型变量但是不初始化；

```cpp
struct_name p2;
```

#### 引用操作
引用操作结构体变量和子变量或者称作成员变量；

规范：`结构体变量.子变量;`

```cpp
cout << p.id << endl; //123
p.id = 456;
cout << p.id << endl; //456
cout << p.name << endl; //name
```

#### demo

```cpp
//定义结构体  
struct struct_name{  
    int id;  
    char name[25];  
};  
//定义结构体类型变量  
struct_name p = {  
        123,  
        {'g', 'a', 'o'}  
};  
//引用操作结构体变量和子变量  
cout << p.id << endl; //123  
p.id = 456;  
cout << p.id << endl; //456  
cout << p.name << endl; //gao
```


#### 结构体赋值
原理：结构体类型变量之间的赋值与普通类型的变量赋值没有区别的；

```cpp
//定义结构体  
struct struct_name{  
    int id;  
    char name[25];  
};  
//定义初始化结构体类型变量  
struct_name p1 = {  
        123,  
        {'g', 'a', 'o'}  
};  
//定义不初始化  
struct_name p2;  
//结构体类型赋值  
p2 = p1;  
  
//引用操作结构体变量和子变量  
cout << p2.id << endl; //123  
p2.id = 456;  
cout << p2.id << endl; //456  
cout << p2.name << endl; //gao
cout << p1.id << endl; //123
```

代码分析：
本质上是将p1在内存的资源复制一份给p2所在的内存空间；

#### 结构体变量做函数参数
本质：是将结构类型变量复制一份赋给函数到函数所在的内存空间区域；

```cpp
//定义结构体  
struct struct_name{  
    int id;  
    char name[25];  
};  
  
void test(struct_name p2)  
{  
    cout << p2.id << endl; //123  
    p2.id = 456;  
    cout << p2.id << endl; //456  
    cout << p2.name << endl; //gao
}  
  
/**  
 * 结构体类型变量-2  
 * @return */int main()  
{  
  
    //定义初始化结构体类型变量  
    struct_name p1 = {  
            1234,  
            {'g', 'a', 'o'}  
    };  
    test(p1);  
    //引用操作结构体变量和子变量  
    cout << p1.id << endl; //123  
  
    return 0;  
}
```

代码分析：
1、这里的结构体定义在main函数外面，是全局结构体；

2、这个与数组作为参数有本质的不同，数组做参数传递的是指针，而结构体是复制一份给函数；

3、函数内结构体类型的变量是局部变量；也可以用static修饰；

#### 结构体变量做函数返回值
本质：是将函数的结构体变量复制一份赋给接收函数返回值的变量所在的内存空间中；

```cpp
//定义结构体  
struct struct_name{  
    int id;  
    char name[25];  
};  
  
struct_name test()  
{  
    //定义初始化结构体类型变量  
    struct_name p = {  
            1234,  
            {'g', 'a', 'o'}  
    };  
    return p;  
}  
  
/**  
 * 结构体类型变量-2  
 * @return */int main()  
{  
    //定义结构体类型变量  
    struct_name p;  
    p = test();  
    //引用操作结构体变量和子变量  
    cout << p.id << endl; //1234  
    cout << p.name << endl; //gao  
  
    return 0;  
}
```

代码分析：
与结构体变量赋值给函数之间是互逆的思路；


#### 结构体变量与指针

->指向运算符

#### 结构体类型数组

#### 结构体类型的意义
1、在c/cpp中结构体类型用到的非常多；

## 结论
1、结构体变量的特性与普通变量特性是一致的；