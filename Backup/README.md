# Neo4j 自动化安装与部署

本项目是由 [Websoft9](http://www.websoft9.com) 研发的 [Neo4j](https://neo4j.com) 自动化安装程序，开发语言是 Ansible。使用本项目，只需要用户在 Linux 上运行一条命令，即可自动化安装 Neo4j，让原本复杂的安装过程变得没有任何技术门槛。  

本项目是开源项目，采用 LGPL3.0 开源协议。

## 配置要求

操作系统：目支持Ubuntu18.x  
硬件配置：最低2核4G，40G系统盘空间，否则无法运行

更多请参考官方 [System requirements](https://neo4j.com/docs/operations-manual/current/installation/requirements/)

## 组件

包含的核心组件为：Neo4j Server, Java, Nginx

更多请见[参数表](/docs/zh/stack-components.md)

## 本项目安装的是 Neo4j 最新版吗？

本项目采用官方提供的在线 deb 安装包，Neo4j 官方会定期维护Neo4j 的版本，即每一次安装均可保证为 Neo4j 官方发布的最新稳定版([查看版本号](https://neo4j.com/download-center/#community))。

## 安装指南

登录 Linux，运行下面的**命令脚本**即可启动自动化部署，然后耐心等待，直至安装成功。

```
#非 root 用户登录后，需先提升成为 root 权限
sudo su -

#自动化安装命令
wget -N https://raw.githubusercontent.com/Websoft9/linux/master/ansible_script/install.py ; python install.py playb=neo4j url=https://github.com/Websoft9/ansible-neo4j.git init=0 ansible=y

```

注意：  

1. 自动化脚本需服务器上已经安装 Python 2.7 或以上版本方可运行，一般操作系统会自带 Python。如果无法运行，系统会提示用户先安装 Python，再运行自动化安装命令。
2. 由于自动化安装过程中有大量下载任务，若网络不通（或速度太慢）会引起下载失败，从而导致安装程序终止运行。此时，请重置服务器后再次尝试安装，若仍然无法完成，请使用我们在公有云上发布的 [Neo4j 镜像](https://apps.websoft9.com/neo4j) 的部署方式

## 文档

文档链接：https://support.websoft9.com/docs/neo4j

## FAQ

- 命令脚本部署与镜像部署有什么区别？请参考[镜像部署-vs-脚本部署](https://support.websoft9.com/docs/faq/zh/bz-product.html#镜像部署-vs-脚本部署)
- 本项目支持在 Ansible Tower 上运行吗？支持