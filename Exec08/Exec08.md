## **Exec08的WP**

**注意事项：请在VMware Workstation软件中完成赛题**

请选手打开VMware Workstation软件-“设置”-“虚拟网络编辑器”打开VMware的VMnet8，也就是NAT模式，依次设置子网IP为192.168.234.0，点击“应用”，点击“确定”。完成设置后开始进行实验。

请使用虚拟机EXEC08、Kali Linux完成实验。

如发生因错误操作需要清理环境重新进行实验，请选手通过“虚拟机”-“快照”进行还原环境后重新开始实验。

请按要求完成以下题目：

服务器场景：EXEC08；服务器场景操作系统：未知；FTP用户名:anonymous 密码：空。

1、通过VMware打开EXEC08，服务器进行操作，根据实际情况，回答以下问题1-3。

问题1：查询本服务器中的网络模式。

NAT

问题2：查询本服务器的账号、密码。

root

admin123!@#

问题3：请写出查询服务器的IP地址的命令并写出本服务器所在的IP网段。

ifconfig

192.168.234.0/24

![1img](https://oss.edu.sangfor.com.cn/file/20240704/240704210453848zk282.jpg)

## **第一个Flag**

Sangfor{nat+root\\admin123!@#+ifconfig\\192.168.234.0/24}

![im1g](https://oss.edu.sangfor.com.cn/file/20240704/240704210453983vkjk6.jpg)

2、完成以下操作并根据要求进行记录。进入Kali Linux操作系统（**提醒**：用户名root和密码123），通过Kali Linux操作系统从服务器EXEC08的FTP上下载attack.pcapng数据包文件。根据实际情况，回答问题4-8。

问题4：请写出查询Kali Linux与EXEC08服务器连通性的命令并完成连通性测试。

问题5：在Kali Linux上对EXEC08服务器的ftp服务进行访问。

问题6：请查看EXEC08服务器的ftp根目录的文件信息。

问题7：请下载attack.pcapng数据包文件，写出下载命令。

问题8：请描述attack.pcapng数据包文件的权限。请描述pub的权限。

![1img](https://oss.edu.sangfor.com.cn/file/20240704/240704210454024kdysj.jpg)

## **第二个Flag**

Sangfor{ls+get attack.pcapng+rw-r–r--}

![1img](https://oss.edu.sangfor.com.cn/file/20240704/240704210454046sepiv.jpg)

3、查看数据包文件attack.pacapng，分析目标服务器相关应用及操作系统版本。并回答问题9-18；

问题9：请查看Kali Linux操作系统的当前工作目录，并截图。

pwd

问题10：请打开Kali Linux操作系统中当前工作目录的attack.pcapng文件，并截图。

wireshak attack.pcapng

问题11：根据数据包的文件，目前服务器中Web服务器中间件引擎是什么？

Apache 2.2.15(CentOS)

问题12：根据数据包的文件，目前服务器中Ftp服务器中间件引擎是什么？

vsFTPd 2.3.4

问题13：vsftp2.3.4中间件的后门端口是什么？

6200

## **第三个Flag**

Sangfor{pwd+wireshak attack.pcapng+apache/2.2.15(centos)+vsftpd/2.3.4+6200}

![1img](https://oss.edu.sangfor.com.cn/file/20240704/240704210454077ryajo.jpg)

问题14：根据相关记录，该攻击者获得系统权限后，输入的第一条命令是什么？

id

问题15：根据相关记录，该攻击者获得系统权限后，输入的第二条命令是什么？

uname -a

## **第四个Flag**

Sangfor{id+uname -a}

![1img](https://oss.edu.sangfor.com.cn/file/20240704/240704210454092wbaa8.jpg)

问题16：根据相关记录，该攻击者获得系统权限后，输入的第三条命令是什么？

pwd

问题17：根据相关记录，该攻击者获得系统权限后，输入的第四条命令是什么？

whoami

## **第五个Flag**

Sangfor{pwd+whoami}

![img1](https://oss.edu.sangfor.com.cn/file/20240704/240704210454118218u9.jpg)

问题18：根据相关记录，该攻击者获得系统权限后，输入的第二条命令后返回结果中#号前的字符是什么？

Linux localhost.localdomain 2.6.32-504.el6.i686

![i1mg](https://oss.edu.sangfor.com.cn/file/20240704/240704210454135hu5ck.jpg)

![i11mg](https://oss.edu.sangfor.com.cn/file/20240704/240704210454166w188p.jpg)

## **第六个Flag**

Sangfor{Linux localhost.localdomain 2.6.32-504.el6.i686}

![i1mg](https://oss.edu.sangfor.com.cn/file/20240704/240704210453951v51wv.jpg)