# 结构体
概念：是一次定义一组变量的自定义数据格式

## 1、结构体类型与结构体变量
结构体变量也可以称作结构体类型变量；

## 2、定义规范

```cpp
struct 结构体名 {
	数据类型 变量名1;
	数据类型 变量名2;
	数据类型 变量名3;......
};
```

1、通过结构体定义的变量称作结构体类型变量，简称结构体变量；

2、结构体内定义的变量是也可以称作结构体变量的子变量或者是成员变量；


## 3、声明定义结构体

```cpp
struct struct_name{
	int id;
	char name[25];
};
```

1、`struct`是关键字；

2、`struct_name`是结构体名；

3、`int id;`和`char name[25];`是成员变量；

## 4、声明定义结构体变量
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

1、struct_name是结构体名；

2、p是结构体类型变量名；

## 5、结构体变量的操作
引用操作结构体变量以及子变量；

### 5.1、访问规范

`结构体变量名.子变量名;`

```cpp
cout << p.id << endl; //123
p.id = 456;
cout << p.id << endl; //456
cout << p.name << endl; //name
```

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

## 6、结构体赋值
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

## 7、结构体变量做函数参数
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

## 8、结构体变量做函数返回值
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

## 9、结构体变量与指针
就是指向结构体变量的指针；

定义：`结构体名 \*指针变量名 = &结构体变量名;`

```cpp
//定义结构体  
struct person{  
    int id;  
    char name[25];  
};  
  
person one = {  
        789,  
        {'g', 'a', 'o'}  
};  
cout << one.id << endl; //789  
person *p_on = &one;  
cout << (*p_on).id << endl; //789  
//cout << *p_on.id << endl; //非法代码
cout << p_on->id << endl; //789  
p_on->id = 123;  
cout << p_on->id << endl; //123
```

代码分析：
1、`cout << *p_on.id << endl;`是非法代码，因为\*p_on.id这个表达式会先运算p_on.id，但是p_one是指针所以找不到成员变量； 

2、`(\*p_on).id;`表达式可以简化成`p_on->id;`，`->`是指向运算符；

## 10、 结构体类型数组
结构体类型的数组；

定义：结构体名 数组名[n];n是数组元素的边界；

```cpp
//定义结构体  
struct person{  
    int id;  
    char name[25];  
};  
  
person rows[3] = {  
        {  
                123,  
                {'g', 'a', 'o'}  
        },  
        {  
                456,  
                {'w', 'a', 'n', 'g'}  
        },  
        {  
                789,  
                {'y', 'a', 'n', 'g'}  
        }  
};  
  
person *p = rows;  
  
cout << p->id << endl; //123  
p++;  
cout << p->id << endl; //456  
p++;  
cout << p->id << endl; //789
```

代码分析：
1、注意定义个rows不是二维数组，只是rows数组的元素是结构体变量；

2、指针p初始化的时候指向的内容是rows[0]；

3、不断的p++就不断的指向下一个rows数组的元素；

## 11、结论
1、结构体变量的特性与普通变量特性是一致的；

2、结构体类型的意义是在c/cpp中结构体类型用到的非常多；
