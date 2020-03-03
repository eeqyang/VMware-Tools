## Fedora 9安装VMware Tools报错及进入不了图形界面的解决方案
### 问题一：出现以下报错提醒时‍

	Searching for a valid kernel header path...
		
	The path "" is not valid.

原因：缺少kernel-devel，即缺少头文件.h

解决方法：

1. 查看kernel版本：
`uname -r`

2. 查看kernel-devel版本：
`rpm -q kernel-devel`

3. 安装或更新kernel-devel至与kernel相同的版本（虚拟机需联网）
`yum install kernel-devel-$(uname -r)`   
其中$(uname -r)是第一步查看的kernel版本号。  

4. 重新安装VMware Tools，若没有更改kernel版本，则将路径设置为
`/lib/modules/(当前版本号)/build/include` 
 ---
### 问题二：出现下述图片内错误时，且关机后无法进入图形界面
![](https://i.imgur.com/mHveXV7.png)

原因：安装的VMware Tools版本过高。

解决方法：需要安装低版本的VMware Tools。
下面给出VMwareTools-8.4.6-385536.tar的下载链接.

[github-VMwareTools-8.4.6-385536.tar](https://github.com/eeqyang/VMware-Tools/blob/master/Link%20Adress.txt)

[gitee-VMwareTools-8.4.6-385536.tar](https://gitee.com/eeqyang/VMware-Tools/blob/master/Link%20Adress.txt)

另外，若要将此文件传输到虚拟机中，

- 方法一：
