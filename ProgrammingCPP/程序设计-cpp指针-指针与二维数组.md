# 指针与二维数组

## 1、二维数组名的本质
二维数组名是指向内容是二维数组的第一个子数组；

```cpp
int a[3][5] = {
        {1, 2, 3, 4, 5},  
        {6, 7, 8, 9, 10},  
        {11, 12, 13, 14, 15}  
};  
cout << a << endl; //0x7ffe089814f0  
cout << a + 1 << endl; //0x7ffe08981504  
cout << a[0] << endl; //0x7ffe089814f0  
cout << a[0] + 1 << endl; //0x7ffe089814f4，本质上是+ 4，可以看出来a[0]是指向a[0]数组的第一个元素的指针；  
cout << &a << endl; //0x7ffe089814f0  
cout << &a + 1 << endl; //0x7ffe0898152c
```

代码分析：
a与a[0]与&a都是地址0x7ffe089814f0的指针常量；但是所指向的内容是不同的；

1、a + 1输出0x7ffe08981504是0x7ffe089814f0+20字节，说明a指向的内容是a[0]这个数组，因为这个数组有5个int(4个字节)的元素，所以跨越内存区间是4x5=20个字节；

2、a[0] + 1输出0x7ffe089814f4是0x7ffe089814f0 + 4字节，说明a[0]指向的内容是a[0]数组的第一个元素，所以跨越4个字节内存区间；

3、&a + 1输出0x7ffe0898152c就是0x7ffe089814f0 + 60字节，说明&a指向的内容是二维数组a，因为二维数组a定义了内存区间是3x5个int所占用的区间，也就是3x5x4=60，固所以跨域了60个字节内存区间；

小结：
a与&a[0]等价；
a[0]与&a[0][0]等价；
a[0]与\*a等价；
a[0][0]与\*\*a等价；

## 2、三规律
1、数组名相当于数组第一个元素的指针；

2、&E相当于把E的管辖范围上升了一个级别；

3、\*E相当于把E的管辖范围下降了一个级别；

## 3、访问二维数组元素
定义了n和元素数组类型的指针变量：int (\*p)[n];
意义：可以通过p[i][j];可以用简化的方式访问p指针的指向的内容；
