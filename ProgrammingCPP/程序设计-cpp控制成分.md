# cpp控制成分

## 1、顺序
是cpp中最基础也是最常见的流程控制，就是带上之上而下的顺序执行控制结构

```cpp
int a = 1;
int b = 2;
int c = 3;
```

程序分别执行了a的初始化然后是b的初始化然后是c的初始化。这个就是顺序执行控制结构。


## 2、判断
以条件作为判断依据的程序执行结构。

### 2.1、if判断

```cpp
//if判断语句
int a = 1;
int b = a + 1;
if (a > b) {
	cout << "a大于b" << endl;
} else if (a < b) {
	cout << "a小于b" << endl;
} else {
	cout << "a等于b" << endl;
}
```

### 2.2、switch判断

```cpp
//switch分支判断
int a = 2;
switch (a)
{
    case 1:
        cout << "a是1" << endl;
        break;
    case 2:
        cout << "a是2" << endl;
        break;
    default:
        cout << "a未知" << a << endl;
        break;
}
```

这里注意：break击穿。

## 3、循环

### 3.1、for循环

```c++
int array_loop[] = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21};
for (int i = 0; i < 10; i++)
{
	cout << "i:" << i << ";array_loop:" << array_loop[i] << endl;
}
```

使用for循环遍历array_loop一维数组。for循环代码块中的局部变量在不同的编译器中有不同的理解。以前的版本变量i的作用域是整个函数，08年后for循环的局部变量的作用域限定for循环的代码块中。


```cpp
for(;;)
{
	code;
}
```

这样的for循环是死循环，不判断for循环中的条件表达式，不断的执行代码块。

### 3.2、while循环
while循环容易造成死循环，因为只要while条件为真那么就会执行代码块。

```cpp
int b = 0;
while (b < 100)
{
	cout << "b:" << b << endl; //输出1到100之间的正整数
	b += 1;
}

```

上述代码等价于：

```cpp
int b = 0;
while ( ++ b < 100) //这个while判断表达式会先执行 `b < 100` 然后执行 `++b`
{
    cout << "b:" << b << endl;
}
```


### 3.3、do while循环
就是先不执行while的判断表达式，直接先运行然后再去判断的循环语句。

### 3.4、goto语句
特点：无条件转向语句。
拓展：在汇编语言中也有goto语句，这就让汇编语言也可以实现各种循环逻辑。
不足：从软件工程的层面出发不建议在高级语言程序中使用goto语句，goto语句使程序不便于阅读和理解，代码结构不清晰直观。goto也不利于**程序正确性的证明**

历史：
1965年IFIP会议上Dijkstra提出‘程序的质量与程序中包含goto语句的数量成反比’，但是当时FORTRAN广泛使用，而goto是FORTRAN的支柱逻辑。
六七十年代的计算机性能比较低下，所以比较重视程序的执行效率，而goto是能够提升程序的效率的，当然提升的也是非常有限，所以被大量的使用和保留，但是现在程序已经不限于一点点的算力的束缚。
1974年Donald Ervin Knuth高德纳全面的总结是：不加限制的使用goto会让程序难以理解，在不破坏程序结构性的前提下为了提升程序效率有控制的使用goto是有必要的。


### 3.5、break语句
break语句只能跳出本loop，但是其他语言是可以在break numbner;设置一个整数参数，决定跳出第几层循环，从所在循环层数1为起始。

### 3.6、continue语句
C++ 中的 **continue** 语句有点像 **break** 语句。但它不是强迫终止，continue 会跳过当前循环中的代码，强迫开始下一次循环。

对于 **for** 循环，**continue** 语句会导致执行条件测试和循环增量部分。对于 **while** 和 **do...while** 循环，**continue** 语句会导致程序控制回到条件测试上。

