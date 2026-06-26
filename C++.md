# 1 内存相关

1. C/C++ - 如何比较两块内存中内容是否相同？（头文件、函数原型、注意事项）

```c++
#include<cstring>
#include<string.h>
int memcmp(const void * ptr1, const void * ptr2, size_t num);
```

​	注意事项：**无法用于比较带填充的结构体**。对于实际值相同的两个结构体，填充部分垃圾值可能导致比较失败。

# 2 字符串相关

1. C/C++ - 如何获取字符串中某个字符最后出现的位置？

```c++
//c
#include<string.h>
char * strrchr(const char * src, int c);
//c++
#include<string>
size_type string:rfind(char c, size_type pos = npos) const noexcept;
```

* 返回值：
  * `strrchr()`成功返回字符c在字符串中最后的位置指针；失败返回NULL。
  * `rfind()`成功返回字符c在字符串中最后的位置；失败返回`npos`；`npos`查找开始的位置，默认为-1。

2. C/C++ - `stringstream`作用是什么？头文件？注意事项？

​	`stringstream`将字符串当作流设备，实现内存格式化读写。头文件是`<sstream>`。

​	注意事项：**清空误区**，复用统一对象时，必须同时调用`ss.clear()`和`ss.str("")`来清空`stringstream`。

3. C/C++ - 使用`stringstream`处理序列化数据时，如何避免数据黏连？

```c++
istringstream << data << "";
ostringstream >> data;
```
