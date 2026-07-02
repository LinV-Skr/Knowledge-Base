1. QTextCursor在Qt中的功能是什么？

​	光标，模拟用户在实际使用过程中的光标移动、选取等功能。

# 1 QTime

1. Qt - 如何获取当前时间？

```c++
#include<QTime>
static QTime QTime::currentTime();
```

2. Qt - QTime默认构造后是否有效？如何判断其是否有效？

​	默认构造后为无效。

```c++
#include<QTime>
bool QTime::isValid() const;
```

3. Qt - 如何获取n秒后的时间？

```c++
#include<QTime>
QTime QTime::addSecs(int secs) const;
```

4. Qt - 通过控制时间间隔，n秒内响应用户操作一次，该使用`QTime::addSecs()`还是`QTime::secsTo()`？

  `secsTo`是更好的选择。

* **逻辑更清晰**：`secsTo` 直接计算时间差，代码可读性更高，更符合直觉。

* **精度更可靠**：`QDateTime` 的 `secsTo` 能正确处理跨天、跨月甚至闰秒等特殊情况。而如果用 `QTime` 的 `addSecs`，一旦跨越午夜（00:00），计算结果会直接“绕回”，导致逻辑错误。


5. Qt - 如何获取信号发送对象？

```c++
qobject_cast<<发送者类型>*>(sender());
```

# 2 QDialog

1. Qt - QProgressDialog，`setWindowTitle`、`setWindowIcon`未生效，该如何解决？

# 3 位置

1. Qt - 如何获取当前窗口的中心位置？

```c++
QPoint center = this->window()->geometry().center();
```

# 4 继承关系

1. Qt - QWidget、QMainWindow、QDialog之间的继承关系是怎样的？

<img src="..\KnowledgeBase\Img\Qt继承关系.png" style="zoom:33%;" />
