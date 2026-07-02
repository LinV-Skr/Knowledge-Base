# 1 内存

1. C/C++ - 如何比较两块内存中内容是否相同？（头文件、函数原型、注意事项）

```c++
#include<cstring>
#include<string.h>
int memcmp(const void * ptr1, const void * ptr2, size_t num);
```

​	注意事项：**无法用于比较带填充的结构体**。对于实际值相同的两个结构体，填充部分垃圾值可能导致比较失败。

# 2 字符串

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

# 3 编译

1. C/C++ - g++和gcc的区别是什么？

​	在编译阶段，g++/gcc没有区别，g++底层也是调用gcc。但是在链接阶段，由于gcc不能链接c++专属的库，因此对于c++程序而言，只能用g++链接。

​	因此，对于c程序，通常使用gcc，对于c++程序，通常使用g++。

2. C/C++ - g++/gcc编译流程中，编译和汇编的区别是什么？

- **编译（Compilation，狭义）**：将高级语言（`.c`/`.cpp`）源码翻译成**汇编语言**（`.s` 文件）。
- **汇编（Assembly）**：将汇编语言（`.s` 文件）翻译成**机器指令码**（`.o` 目标文件）。

3. C/C++ - g++/gcc编译时，如何指定`include`包含文件的搜索目录？

```bash
gcc -I <DirectoryPath>
```

4. C/C++ - g++/gcc编译时，如何生成调试信息、可以被调试器调试？

```bash
gcc -g
```

