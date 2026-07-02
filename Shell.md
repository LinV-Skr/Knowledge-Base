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

2. SSH - 如何查看密钥中的指纹信息？

```shell
ssh-keygen -lf ~/.ssh/id_ed25519.pub
```

* `-l`：list，显示公钥的指纹信息；
* `-f`：file，指定文件路径。

3. SSH - 指纹信息的作用是什么？

* 验证远程服务器身份（防范中间人攻击）；
* 验证本地公私钥是否配对；
  * `ssh-keygen -lf ~/.ssh/id_rsa`
  * `ssh-keygen -lf ~/.ssh/id_rsa.pub`
* 指纹更简洁，用于筛选用户对应的公钥。

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

9. Linux Shell - `source ~/.bashrc`的作用是什么？

​	在当前终端会话中，立即执行一遍`.bashrc`文件里的所有命令，让修改后的配置即时生效。

10. Linux Shell - 如何查看服务日志？（以`gitea`举例说明）

```shell
journalctl -u gitea -n 50 --no-paper
```

​	`journalctl`，全称Journal Control（日志控制工具），是`systemd`自带的一个日志查看命令，用户查询和管理`systemd`的日志系统（即`Journal`）。

* `-u`，过滤单元（Unit）。
* `-n`，限制次数（Number）。
* `--no-paper`，禁用分页器。

11. Linux Shell - 如何实时跟踪显示文件末尾内容？

```shell
tail -f
```

* `-f`：follow，实时跟踪文件末尾新增内容。

12. Linux Shell - 如何输出指令在`$PATH`对应的路径？

```shell
# which <指令名>
which ssh-keygen
#  输出/usr/bin/ssh-keygen
```

