
# 指针与数组

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

结论：
