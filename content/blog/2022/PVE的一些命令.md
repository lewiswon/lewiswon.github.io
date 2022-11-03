+++
title = "PVE的一些命令"
date = 2022-08-18
+++

## 0x00 前言
在N5105的软路由上装了 `Proxmox PVE` 来管理整个环境，顺便装了 Homeassistant，但是不明原因的连续两次出现虚拟机死掉，从 PVE 的 WebUI 上操作各种超时和失败，Google 了一下，发现可以进入 PVE 的 Shell 进行操作，所以就在这里记录一些相关的操作，以免后面再次遇到。

## 0x01 直接杀死虚拟机的进程
找到虚拟机的PID
```bash
# VIMID为虚拟机的ID,在 PVE 的 WebUI 上可以看到
ps aux | grep '/usr/bin/kvm -id VMID'
```
杀死虚拟机的进程
```bash
kill -9 PID
```
杀死了锁定他的进程后，就可以使用 qemu 的命令，对虚拟机进行停止了。
```
qm stop VMID
```