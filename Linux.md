# 1 Service

1. Linux - 如何设置应用自启动？

* 添加\<AppName\>.server文件；
* 重新加载`systemd`配置。
  * `sudo systemctl daemon-reload`；
* 设置为自启动。
  * `sudo systemctl enable <AppName>.service`；
  * `sudo systemctl start <AppName>.service`。

2. Linux - 服务文件（.service），`After=network.target`作用是什么？

​	定义服务启动的先后顺序，在`network.target`启动之后再启动。

3. Linux - 服务文件（.service），`Type=forking`的作用是什么？

​	告诉systemd，这个服务启动后，主进程会先创建子进程，然后自己退出。

4. Linux - 服务文件（.service），`PrivateTmp=true`的作用是什么？

​	为服务分配一个“私有的、隔离的”临时目录空间。

5. Linux - 服务文件（.service），`WantedBy=multi-user.target`的作用是什么？

​	指定服务在哪个系统“运行级别“下被触发启动。`multi-user.target`代表系统多用户命令行模式。

6. Linux - 服务文件（.service），`User=git Group=git`的作用是什么？

​	身份隔离，强制启动进程放弃root权限，以普通用户Git的身份运行，更加安全。

# 2 Compile

1. Linux - 源码编译环境下，`configure`的作用是什么？

​	扫描系统环境，根据扫描结果和定制要求，生成一份专属Makefile文件，为后续的make编译做准备。

2. Linux - 源码编译环境`configure`，如何指定编译安装路径？

```shell
./configure --prefix=<filePath>
```