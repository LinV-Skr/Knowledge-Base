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

​	`QProgressDialog::setWindowTitle`、`QProgressDialog::setWindowIcon`设置生效需满足以下两个条件：

* 父对象是顶层窗口。
  * 顶层窗口为`QMainWindow`、`QDialog`或者父对象为NULL的`QWidget`；
* 父对象未设置`FramelessWindowHint`；

​	若不满足则无法生效，需将`QProgressDialog`父对象设置为NULL，才能生效。

```c++
QProgressDialog progressDialog(NULL);
progressDialog.setAttribute(Qt::WA_DeleteOnClose);
```

# 3 位置

1. Qt - 如何获取当前窗口的中心位置？

```c++
QPoint center = this->window()->geometry().center();
```

2. Qt - `QProgressDialog`如何移动位置？

```c++
void QWidget::move(int x, int y);
```

# 4 继承关系

1. Qt - QWidget、QMainWindow、QDialog之间的继承关系是怎样的？

<img src=".\Img\Qt继承关系.png" style="zoom:33%;" />

# 5 QTable

1. Qt - `QAbstractTable`如何设置行标题？

​	重写`QAbstractTableModel::headerData(int section, Qt::Orientation, int role)`，执行返回对应行列值。

```c++
QVariant MyTableModel::headerData(int section, Qt::Orientation orientation, int role) const
{
	// 只处理显示文本的角色
    if(role == Qt::DisplayRole) 
    {
        // 判断请求的是行标题（垂直方向）还是列标题（水平方向）
        if(orientation == Qt::Vertical)
        {
            // 返回你想要为这一行显示的文本
            // section 参数就是行号，从 0 开始
            return QString ("第 %1 行").arg(section + 1);
        }
        
        // 如果是列标题，则调用父类默认行为或自定义处理
        if(orientation == Qt::Horizontal)
        {
			// 例如，根据 section 返回不同的列标题
            if(section == 0) return QString("列 A");
            if(section == 1) return QString("列 B");
            return QString("列 %1").arg(section + 1);
        }
    }
    // 对于其他角色，返回空 QVariant
    return QVariant();
}
```

# 6 QWidget

1. Qt - 如何设置窗口不显示外边框、标题栏？

```c++
#include<QWidget>
void QWidget::setWindowFlags(Qt::WindowFlags type);
//  Type取Qt::FramelessWindowHint
```

