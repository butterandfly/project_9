# 安装Gentoo

## 启动livecd
```
gentoo dopcmcia
```

## 连接无线
首先你可以通过`ifconfig`和`iwconfig`查看你的网卡驱动是否已安装，然后用`iwlist`查看附近的无线：
```
iwlist scanning | grep SSID