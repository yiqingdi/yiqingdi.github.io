---
title: V2ray搭建教程
date: 2021-07-12 16:12:07
tags: V2ray
categories: 教程
---
获取root权限：
sudo -i
=======================================
##Debian更新系统##

apt update -y
##CentOS更新系统##

yum install epel-release -y

yum update -y
##CentOS更新系统##

yum update -y

yum install -y curl
=======================================<!--more-->

V2ray一键安装指令：
bash <(curl -s -L https://git.io/v2ray.sh)

如果提示 curl: command not found ，那是因为你的 VPS 没装 Curl

ubuntu/debian 系统安装 Curl 方法: apt-get update -y && apt-get install curl -y

centos 系统安装 Curl 方法: yum update -y && yum install curl -y

安装好 curl 之后就能安装脚本了


备注:非常重要

使用Oracle Cloud free 免费云搭建了v2ray /  shadowsockR， 在 子网 -> 安全列表 -> 入网规则 里也打开了对应的端口，但还是无法科学上网。

原来oracle cloud与 aws等云不同，需要关闭防火墙或iptable。


解决方法：

centos操作如下：

#停止firewall
systemctl stop firewalld.service
#禁止firewall开机启动
systemctl disable firewalld.service
#关闭iptables
service iptables stop
#去掉iptables开机启动
chkconfig iptables off

oracle Linux操作如下：
#停止firewall
systemctl stop firewalld.service
#禁止firewall开机启动
systemctl disable firewalld.service

ubuntu操作如下：
#Oracle自带的Ubuntu镜像默认设置了Iptable规则，关闭它
apt-get purge netfilter-persistent
reboot
#强制删除
rm -rf /etc/iptables && reboot



