# 1 内存相关

1. C++ - 如何比较两块内存中内容是否相同？（头文件、函数原型、注意事项）

```c++
#include<cstring>
#include<string.h>
int memcmp(const void * ptr1, const void * ptr2, size_t num);
```

​	注意事项：**无法用于比较带填充的结构体**。对于实际值相同的两个结构体，填充部分垃圾值可能导致比较失败。

2. C++ - 使用`stringstream`处理序列化数据时，如何避免数据黏连？

```c++
istringstream << data << "";
ostringstream >> data;
```

