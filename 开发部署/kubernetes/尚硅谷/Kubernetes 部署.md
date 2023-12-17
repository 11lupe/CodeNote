## Kubernetes 部署

[TOC]

### 1.准备 环境

**系统环境：三台centos7环境**

192.168.5.10 k8s-master

192.168.5.20 k8s-node1

192.168.5.21 k8s-node2

**分别修改3台主机名**

```bash
hostnamectl set-hostname k8s-master
```

```bash
hostnamectl set-hostname k8s-node-1
```

```bash
hostnamectl set-hostname k8s-node-2
```

**增加修改host解析（3台机器都要执行）**

```bash
vim /etc/hosts
```

```
192.168.6.129 k8s-master
192.168.6.130 k8s-node-1
192.168.6.131 k8s-node-2
```

**关闭防火墙**

关闭防火墙

```bash
systemctl stop firewalld
```

关闭selinux

```bash
setenforce 0
```

关闭swap

```bash
# 临时关闭
swapoff -a
# 永久关闭
vim /etc/fstab
```

