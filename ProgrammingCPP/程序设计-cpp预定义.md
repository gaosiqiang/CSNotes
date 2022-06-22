# 程序设计-头文件

## 1、预定义

c/cpp文件的预定义部分：也就是文件头部分或头文件。

```cpp
#include <iostream>
using namespace std;
```

这个是主函数部分
```cpp
int main()
{
	函数体;
}
```

c/cpp的ISO标准是编译器编译c&cpp的编译标准而非代码语法标准。

cout本质是个cpp对象，当 cout << xxxx; 等价于 cout.构造函数(xxxx);。

## 2、文件的引用
cpp中使用 include 引用文件，引用的文件名用"文件名"双引号，而系统类库是<系统类库>尖括号。这是因为引用的名称是双引号编译器会优先查找自定义函数库，而尖括号编译器会优先查找系统函数库。
