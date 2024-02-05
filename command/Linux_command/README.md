# Linux 常用命令
本文介绍了一些常用的 Linux 命令，可用于在终端中执行各种操作和管理任务。

## 目录操作
pwd ：显示当前工作目录的路径。
```
pwd
```

ls：列出当前目录的内容。
```
ls
```

cd ：切换到指定目录。
```
cd
```

mkdir ：创建一个新目录。
```
mkdir
```

rm ：删除指定的文件。
```
rm <file>
```

rm -r ：递归删除指定的目录及其内容。
```
rm -r <directory>
```

cp ：将文件或目录从源位置复制到目标位置。
```
cp <source> <destination>
```

mv ：将文件或目录从源位置移动到目标位置。
```
mv <source> <destination>
```

## 文件操作
cat ：显示文件的内容。
```
cat <file>
```

head ：显示文件的前几行。
```
head <file>
```

tail ：显示文件的最后几行。
```
tail <file>
```

touch ：创建一个新文件。
```
touch <file>
```

nano ：使用文本编辑器 Nano 打开文件进行编辑。
```
nano <file>
```

grep ：在文件中搜索匹配指定模式的行。
```
grep <pattern> <file>
```
du : 查看文件或文件夹大小
```
du -h --max-depth=0 directory
``` 

## 互传文件
### 本地向Linux传文件
* scp命令
```
scp /path/to/local/file username@remote_host:/path/to/destination
```

* sftp
```
sftp username@remote_host
put /path/to/local/file /path/to/destination
```

### Linux向本地传文件
* scp命令
```
scp username@remote_host:/path/to/file /path/to/destination
```
* sftp
```
sftp username@remote_host
get /path/to/file /path/to/destination
```

### 如果需要传输文件夹 就在scp命令后加一个参数-r
下例是Linux向本地传输文件夹
```
scp -r username@remote_host:/path/to/folder /path/to/destination
```

## 系统管理
top：显示系统中正在运行的进程和资源使用情况。
```
top
```

ps：显示当前用户的进程状态。
```
ps
```

kill ：终止指定进程。
```
kill <pid>
```

shutdown：关闭系统。
```
shutdown
```

reboot：重启系统。
```
reboot
```

## 网络管理
ping <host>：测试与指定主机的连通性。
```
ping <host>
```

ifconfig：显示网络接口的配置信息。
```
ifconfig
```

ip addr：显示网络接口的 IP 地址信息。
```
ip addr
```

netstat：显示网络连接和统计信息。
```
netstat
```
查看端口占用情况
```
netstat -apn | grep LISTEN
```
lsof命令查看具体端口占用情况
```
sudo lsof -i :端口号
```

ssh <user>@<host>：通过 SSH 连接到远程主机。
```
ssh <user>@<host>
```
删除ssh host
```
ssh-keygen -R <host>
```
查看防火墙已开放的端口
```
firewall-cmd --zone=public --list-ports
```
添加开放的端口80
```
firewall-cmd --zone=public --add-port=80/tcp --permanent 
```
重载防火墙策略
```
firewall-cmd --reload
```
查看指定的端口（比如）
```
firewall-cmd --zone= public --query-port=80/tcp 
```
删除开放的端口80
```
firewall-cmd --zone= public --remove-port=80/tcp --permanent
```

## 压缩和解压缩
tar -czvf ：将指定目录压缩为 .tar.gz 归档文件。
```
tar -czvf <archive.tar.gz> <directory>
```

tar -xzvf ：解压缩 .tar.gz 归档文件。
```
tar -xzvf <archive.tar.gz>
```

zip ：将指定文件打包为 .zip 压缩文件。
```
zip <archive.zip> <file1> <file2>
```

unzip ：解压缩 .zip 压缩文件。
```
unzip <archive.zip>
```

## 用户及权限管理
添加新用户
```
sudo adduser <username>
```
给用户设置密码
```
passwd <username>
```
给用户设置root权限
```
sudo usermod -aG sudo <username>
```
进入超级用户模式
```
sudo su
```
或者
```
sudo -s
```
退出超级用户模式
```
exit
```
## 查看硬件信息
查看cpu信息
```
cat /proc/cpuinfo
```
或者
```
lscpu
```
查询内存信息
```
cat /proc/meminfo
```
查询硬盘信息
```
df -h
```
查询gpu信息
```
lspci | grep -i vga
```
如果安装了nvdia驱动 则可以执行
```
nvidia-smi
```