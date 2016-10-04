---
title: 虚拟化
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

# 前言
## 概念
一台物理机可以跑多台虚拟机，通过共享宿主机的 cpu、内存、存储、io资源，这种技术就是虚拟化，主要有Hypervisor的程序实现。
## 分类
1. Hypervisor直接运行在物理机上，一般是一个特殊定制的Linux系统。虚拟机都跑在Hypervisor上面。例子：Xen与VMWare的ESXi等。
2. Hypervisor作为一个软件运行在Ubuntu、windows等操作系统中。例如：KVM、VirtualBox、VMWare Workstation等。
3. 最近比较火的容器也可以看成一个小型的虚拟机

# KVM
## 简介
作为一种Hypervisor，KVM全称Kernel-Based Virtual Machine，本身只关注虚拟机和内存的调度，IO和外设都是有Linux内核和QEMU。
## 安装
安装kvm环境，一般需要安装：
qemu-kvm  qemu-system  libvirt-bin  virt-manager  bridge-utils  vlan  
### QEMU
是核心包，包含了cpu、内存、io等虚拟化
### Libvirt
负责管理KVM、Xen、VirtBox等Hypervisor。（openstack的底层就是使用了Libvirt）。包含三部分：API库（可以用于开发高级的管理工具，如virt-manager），命令行工具virsh，后台程序libvirtd（接受处理API请求）
### virt-manager
kvm图形化界面
常用命令：
$ virt-manager
### bridge-utils vlan
用于网络虚拟化，KVM是基于bridge-utils和vlan技术
## 虚拟化原理
