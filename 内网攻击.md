### \[题目信息\]：

| 题目名称 | 题目方向 | 题目难度 |
| --- | --- | --- |
| 内网攻击 | 内存取证 | \*\*\* |

### \[题目writeup\]：

查看内存文件镜像版本

```
python2 vol.py -f baka.raw imageinfo
```

![1720004644156](https://oss.edu.sangfor.com.cn/file/20240704/240704202238269j8776.png)

查看内存文件网络情况

```
python2 vol.py -f baka.raw --profile Win7SP1x64 netscan
```

### 任务一

攻击者使用的恶意样本文件的名称是( )。

![17200048314606](https://oss.edu.sangfor.com.cn/file/20240704/240704202238299qwe8f.png)

beacon.exe为常见的cobaltsrike木马文件

### 任务二

攻击者使用的恶意样本文件所在目录是( )。请提交上两级目录。例如，1.txt所目录为，C:\\Users\\admin\\Desktop\\1.txt，那么请提交，admin\\Desktop\\

```
python2 vol.py -f baka.raw --profile Win7SP1x64 filescan|findstr beacon.exe
```

![1720081889989](https://oss.edu.sangfor.com.cn/file/20240704/240704202238407q16r9.png)

PHPTutorial\\backup\\

### 任务三

攻击者使用的恶意样本监听服务器的端口是( )。

根据任务一可知，答案为Sangfor{11451}

### 任务四

```
python2 vol.py -f baka.raw --profile Win7SP1x64 filescan|findstr beacon
```

转储并提交到在线沙箱平台分析

![1720093588471](https://oss.edu.sangfor.com.cn/file/20240704/240704202238530mjvgz.png)

https://s.threatbook.com/

攻击者使用恶意样本开启的管道名称(/pipe/???-???-???)

python2 vol.py -f baka.raw --profile Win7SP1x64 dumpfiles -Q 0x000000007ed848b0 -D ./dump

![1720094405479](https://oss.edu.sangfor.com.cn/file/20240704/24070420223859875jng.png)

pipe\_name：\\?\\pipe\\MSSE-1126-server

### 任务五

攻击者是否在执行过在注册表中添加权限维持项的命令，如果有，请提交攻击者所添加权限维持项的路径。请提交flag，flag格式Sangfor{注册表路径}，示例，如注册表路径为"HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\xxx"

请提交Sangfor{HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\xxx}

```
python2 vol.py -f baka.raw --profile Win7SP1x64 cmdscan
```

![1720095252026](https://oss.edu.sangfor.com.cn/file/20240704/240704202238642icjgp.png)

![1720089716194](https://oss.edu.sangfor.com.cn/file/20240704/240704202238427tkw6j.png)

答案Sangfor{HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\CurrentVersion\\Run}