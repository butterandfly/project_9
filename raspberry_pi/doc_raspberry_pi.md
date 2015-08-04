# Doc: Raspberry Pi

## 连接树莓派

### 同局域网下查看树莓派ip

```
nmap  -sP 192.168.1.0/24
```

## 基础设置

### Locales
[How to set up a clean UTF-8 environment in Linux](http://perlgeek.de/en/article/set-up-a-clean-utf8-environment)

### 网络

#### 设置静态ip
打开`/etc/network/interfaces`文件，修改eth0的设置：

```
# iface eth0 inet dhcp
# 将eth0设置的static的，并设置ip与网关
iface eth0 inet static
address 192.168.1.88
netmask 255.255.255.0
gateway 192.168.1.1
```

## 搭建NAS（数据中心）
[树莓派搭建NAS](https://github.com/butterandfly/project_9/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE%E6%90%AD%E5%BB%BANAS)

## 使用百度云盘下载、上传内容

### 使用[bypy](https://github.com/houtianze/bypy)