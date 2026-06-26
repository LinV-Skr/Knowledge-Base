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

