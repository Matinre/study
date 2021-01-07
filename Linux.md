# Linux基本命令

## 	创建目录

> mkdir 目录名

## 	查看目录

> ls/ll 目录名

## 	创建文件

> touch 文件名
>
> 多个文件  touch {1..100}.txt

## 	编辑文件

> vim 文件名
>
> ：wq！强制保存退出
>
> ：q 不保存退出

## 	删除文件

> rm -rf 文件名（*代表所有）
>
> rm -f 文件

## 	查看进程

> ps -ef|grep 关键词

## 	kill指定进程

> ps -ef | grep 进程名(或关键字) | grep -v grep | awk '{print $2}' | xargs kill -9

## 	开启apache

> systemctl start/stop/restart httpd

## 	关闭防火墙

> ```
> [root@Apache ~]# systemctl stop firewalld         --临时关闭防火墙 
> [root@Apache ~]# systemctl disable firewalld    --永久关闭防火墙
> ```

## 	关闭selinux

> ```
> [root@Apache ~]# setenforce 0
> setenforce: SELinux is disabled
> ```

## 	压缩解压zip文件

> 压缩：zip -r 压缩后文件名  源文件（zip test.zip test）
>
> 解压：unzip 压缩文件（unzip test.zip）

## 	压缩解压tar文件

> tar -zcvf a.tar.gz file1 file2  #一步到位，连打包带压缩
>
> 各种tar格式的解压
>
> ```
> tar -xvf file.tar #解压 tar包
> 
> tar -xzvf file.tar.gz #解压tar.gz
> 
> tar -xjvf file.tar.bz2   #解压 tar.bz2
> 
> tar -xZvf file.tar.Z   #解压tar.Z
> 
> unrar e file.rar #解压rar
> 
> unzip file.zip #解压zip
> ```

