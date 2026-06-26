1. Linux - 如何设置应用自启动？

* 添加\<AppName\>.server文件；
* 重新加载`systemd`配置。
  * `sudo systemctl daemon-reload`；
* 设置为自启动。
  * `sudo systemctl enable <AppName>.service`；
  * `sudo systemctl start <AppName>.service`。

2. Linux - 服务文件（.service），`After=network.target`作用是什么？

​	定义服务启动的先后顺序，在`network.target`启动之后再启动。