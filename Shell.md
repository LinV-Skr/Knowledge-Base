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

