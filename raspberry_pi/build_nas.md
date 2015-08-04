# 树莓派搭建NAS

## 什么是NAS
NAS的核心功能包括：
* 文件储存与共享
* 文件自动备份
* （可选）迅雷下载

## 硬件准备
### 使用移动硬盘作为存储
我有一个320g的移动硬盘作为NAS的核心存储；但该硬盘非自带电源，而树莓派的usb电压明显不能使该移动硬盘正常运作，所以我还要一个带电源的usb分线器。简单来说材料包括：
* 移动硬盘
* 带电源的usb分线器

## 文件储存
### 使用移动硬盘
具体看：http://www.geekfan.net/2767/
其中的要点包括：
* 挂载我们的硬盘
* 因该硬盘使用的是ntfs格式，所以我们需要安装一个支持ntfs的软件包

#### 开机自动挂载移动硬盘
一个很简单的方法是修改`/etc/fstab`，详细见：http://community.linuxmint.com/tutorial/view/1513

## 文件共享
### 使用samba
具体看：http://www.geekfan.net/2767/
要点包括：
* 安装与设置samba，别忘记向samba添加用户
* 重启、开启samba
* 使用mac等连接samba服务器
* samba的配置文件在：`/etc/samba/smb.conf`

## 文件备份
研究中......

## 迅雷下载
具体见：http://www.dozer.cc/2014/05/raspberry-pi-nas/
要点：
* 下载固件并在树莓派上运行
* 登陆迅雷的远程下载页，输入验证码