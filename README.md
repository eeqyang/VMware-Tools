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

- 方法一：可以先将虚拟机与主机联网使用ftp传输；

- 方法二：或者先安装出错如图所示，但是在不关机的情况下可以使用共享文件，将上述文件通过共享文件转移到虚拟机中。

但是，方法二发现关机后进不了图形界面，可以通过**卸载VMware Tools**解决。login界面登入root账号，再输入以下代码。

**卸载VMware Tools的方法**：

1. 输入`/usr/bin/vmware-uninstall-tools.pl`

2. 输入`system-config-display`，进行分辨率配置，生成/etc/X11/xorg.conf文件。

3. 输入`startx`直接启动或者`reboot`重启

4. 但在安装旧版本VMware Tools之前，先删除/usr/lib/vmware-tools，其方法为`rm -rvf /usr/lib/vmware-tools`
 
最后，重新安装下载的旧版本的VMware Tools，一直点击Enter键完成安装。

