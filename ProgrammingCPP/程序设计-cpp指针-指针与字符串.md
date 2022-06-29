# 指针与字符串
字符串本质上就是字符数组；

## 1、code1

```cpp
int a = 5;  
int *pa = &a;  
  
int b[5] = {1, 2, 3, 4, 5};  
int *pb = b;  
  
char c[5] = {'a', 'b', 'c', 'd', 'e'};  
char *pc = c;  
  
char d[5] = "abcd";  
char *pd = d;  
  
cout << a << endl;  
cout << pa << endl;  
cout << b << endl;  
cout << pb << endl;  
cout << c << endl;  
cout << pc << endl;  
cout << d << endl; //会输出'abcd'；cout操作符会对字符数组元素自动进行拼接处理； 
cout << pd << endl; //会输出'abcd'；  
cout <<static_cast<void*>(c) << endl; //输出地址：0x7fff27a18c20  
cout <<static_cast<void*>(pc) << endl; //输出地址：0x7fff27a18c20  
  
return 0;
```

代码分析：
cout操作符会对字符数组元素自动进行拼接处理；cout只有字符类型数组的才这样处理；

## 2、code2

```cpp
char buffer[100] = "ABC";  
const char *pc = NULL;  
pc = "DEF";
cout << pc << endl; //DEF  
pc++;  
cout << pc << endl; //EF  
cout << *pc << endl; //E  
pc = buffer;  
cout << pc << endl; //ABC  
  
return 0;
```

代码分析：
字符类型指针赋值字符串，可以使用const来修饰也可以不用，具体看编译器。因为字符串字面值是常量，有些编译器会报错；

## 3、字符指针赋值字符串原理

通过程序的运行情况，可知：char \*pc = 
"adc";这种字符串的赋值方式是完全没有问题的。要理解这种赋值方式，首先得理解双引号（特别注意：这个是双引号，不要赋值的时候给弄了个单引号）在这个语句的流程是：

1、申请了空间（在常量区），存放了字符串；

2、在字符串尾加上了"\0"；

3、返回的地址赋值给了char \*pc；


