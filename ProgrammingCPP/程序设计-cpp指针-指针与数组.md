
# 指针与数组
通过探究指针与数组的之间的关系，能更清晰有深度的理解数组的本质；

## 2、指针与数组元素

```cpp
int a[5] = {1, 2, 3, 4, 5};
cout << a[3] << endl; //4
int *p = NULL;
p = &a[3];
cout << *p << endl;//4
*p = 10;
cout << a[3] << endl;//10
```

结论：指针变量指向数组元素与指向普通变量没有区别；

## 2、指针与数组名

```cpp
int a[5] = {1, 2, 3, 4, 5};
cout << a << endl; // 0x7fff7c2a1b10
cout << *a << endl; // 1
cout << &a[0] << endl; // 0x7fff7c2a1b10
cout << a[0] << endl; // 1
```

代码说明：
数组名a是指向数组a的第一个元素的指针，注意是指针；


```cpp
int a[5] = {1, 2, 3, 4, 5};
int *b;
b = a;
int c;
c = a[0];
cout << a << endl; //0x7ffd9b59a360
cout << b << endl; //0x7ffd9b59a360
cout << c << endl; //1
cout << &c << endl; //0x7ffd9b59a35c
cout << &a[0] << endl; //0x7ffd9b59a360
```

代码说明：
`b = a;`只是将数组a的第一个元素的指针赋值给p；
`c = a[0]`是将数组a的第一个元素的值复制赋值给c，由输出的地址可知；


结论：
1、数组名是地址常量也就是指针常量；
1、因为a是常量所以不能被赋值；
2、a与&a[0]等价；

## 3、指针取数组元素值
数组元素的应用一般情况用下标来是使用的，如果通过指针和指针算术运算规则，那么代码的执行效率会更高；

### 总结规律
若定义：
数组 int a[10]; 指针 int \* pointer;

则：
pointer = a; 等价于 pointer = &a[0];
pointer + i; 等价于 a + i; 等价于&a[i];
\*(pointer + i); 等价于 \*(a + i); 等价于 a[i];
pointer[i]; 等价于 \*(pointer + i);

