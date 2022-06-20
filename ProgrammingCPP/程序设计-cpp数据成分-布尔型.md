# 数据成分-布尔型

## 布尔型
布尔型：布尔只占用1一个字节8个bit，只要是非0的数据在布尔逻辑上都是true也就是1，只有8个bit都是0才是false，其他情况都是true。

布尔类型的真值逻辑是，只要是非0的都是true。

布尔类型占用一个字节，在内存中一个byte中所有的bit位都是0是false，其他情况都是true。

| 线位 | 0x0 | 0x1 | 0x2 | 0x3 | 0x4 | 0x5 | 0x6 | 0x7 |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| bit位 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

声明定义：

```c++
bool is_true = true; //true
bool is_false = false; //false
bool is_bool = 1; //true
bool is_bool = 0; //false
int is_bool = true; //1
int is_bool = false; //0
```
