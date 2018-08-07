readme

ansible一键安装k8s10x和k8s11x

1：/etc/ansible/hosts文件解释
-----------------------------------------------------------------------------------------------------------------------------------

[slb]

192.168.150.179 name=slb-179 type=MASTER priority=100 

192.168.150.180 name=slb-180 type=BACKUP priority=90

[k8s-master]

192.168.150.181 name=node01  order=1

192.168.150.182 name=node02  order=2

192.168.150.183 name=node03  order=3

[k8s-node]

192.168.150.184 name=node04

[k8s-all:children]

k8s-master

k8s-node

[all:vars]

local_images=registry.cn-hangzhou.aliyuncs.com/k8sth

k8s_version=1.10.5

vip=192.168.150.186

#type表示keepalived的类型是master或者backp

#priority代表权重，可以自行修改，但是不建议修改，直接修改IP为合适的就行

#name为主机名称，可以自行修改，在系统初始化时会以此添加并配置所有主机的/etc/hosts文件

#order为k8s初始化的顺序，不能修改

#local_images为镜像地址，本人镜像地址包含1.10.0--1.11.1所有的K8S镜像，所以可以不用修改，如果用局域网内部仓库，必须是https的

#k8s_version为需要安装的kubernetes版本号

---------------------------------------------------------------------------------------------------------------------------------------

