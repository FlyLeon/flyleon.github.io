# N1使用openwrt做旁路由

> 最近在拼多多买了一台N1，参照网上说明设置为旁路有，由于上网。操作很简单，不需要usb直连线，固件用就网上大神编译好的。
## N1 降级
- 用HDMI视频数据线将N1盒子和显示器连接起来, 并使用鼠标和键盘将N1盒子连接到主路由的WiFi, 同时记下上面显示的IP地址。
- 点击四下固件版本, 屏幕上提示打开adb。
- 打开电脑,运行降级工具包里的run.bat, 输入数字2并Enter, 随后输入刚刚记下的IP地址, 最后按任意键开始降级. 注意此时电脑要保持联网状态,因为降级工具需要联网获取文件。
- 降级成功后运行激活U盘启动工具包里的N1盒子激活U盘启动.bat,并输入刚刚记下的IP地址即可激活U盘启动. 这里的IP有可能在降级之后发生变化,可以连接显示器再次确认。
## 启动USB制作
可在linux和mac下直接使用`dd`制作，windows下需另下usb制作工具。
```
lsblk  #查看磁盘
dd if=*.img of=/dev/目标盘
```
## 旁路由设置
- 设置网段
修改路由器内网网段连接盒子。也可使用电脑直连，各固件缺省地址不同，将电脑设为一个网段，电脑网关设置为N1地址。
- 修改ip、关闭dhcp、桥连
使用网络浏览器，输入N1地址，打开openwrt设置页面，缺省`root`密码为`password`。打开网络设置-lan，设置你想要静态ip。关闭下面的dhcp和高级设置中的桥连，使用`eth0`。设置好后保存并应用，然后重启N1，使新设置的地址生效。
- 关闭N1的wifi
打开网络设置-wlan，停止wifi。
## 将固件刷入N1盒子
- 用ssh连接盒子
```
ssh root@盒子地址
```
- 刷机
```
./inst-to-emmc.sh
```


