# 1 Ftp Shell

1. Ftp如何删除服务器中，中文名称乱码的文件？

```shell
mdelete *
```

​	对于中文名称乱码文件，使用`delete`已经无法删除，需使用`mdelete`通过通配符来进行删除。

# 2 VxWorks

1. VxWorks如何终止进程？

```shell
rtpDelete <进程ID>
```

2. VxWorks如何打印一次CPU占用率？

```shell
spyReport
```

# 3 SSH

1. SSH - 将本地生成的`id_xx.pub`中的密钥拷贝至服务器后，如何验证`ssh`功能是否配置成功？

```shell
ssh -T -i ~/.ssh/id_xxx.pub 用户名@服务器ip
ssh -T -i ~/.ssh/id_xxx.pub git@github.com
```

* `-i`，全称`identity_file`，指定用于身份验证的私钥文件路径。
* `-T`， 参数的作用是**禁用伪终端（Pseudo-terminal）的分配**。简单来说，它告诉 SSH 客户端：“**不要**为这次连接创建远程端的交互式命令行环境（Shell）”。

# 4 Linux Shell

1. Linux Shell - 如何查看操作系统位数？

```shell
uname -m
#i686 - 32位
#x86 - 64位
```

2. Linux Shell - 如何快速给文件添加执行权限？

```shell
chmod +x <filePath>
```

3. Linux Shell - `tar -zxvf`，每个字段的含义？

* `-z`：通过gzip算法。
* `-x`：解压（extract）。
* `-v`：显示详细过程（verbose）。
* `-f`：指定文件名（file）。

4. Linux Shell - 如何递归修改目录下所有文件的所有者？

```shell
chown -R 
```

5. Linux Shell - 如何增加系统用户？系统用户和普通用户的区别是什么？

``` shell
useradd --system <userName>
```

​	系统用户（UID<1000）主要用于运行后台服务。不会出现在登录界面的欢迎列表中，也没有密码过期的问题。

6. Linux Shell - 新增用户时，如何指定交互式响应shell？

```shell
useradd --shell /bin/bash <userName> 
```

7. Linux Shell - 新增用户时，如何指定并创建用户目录？

```shell
useradd --create-home --home-dir <filePath> <userName>
```
8. Linux Shell - `echo`的作用是什么？

​	将指定的文本或者变量值输出在终端上。

```shell
# 查看变量值
my_var="Hello World"
echo $my_var
```

