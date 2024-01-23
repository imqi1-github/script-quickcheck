手动安装DockerCentOS/RedHat:

1. 删除之前安装的docker

```bash
yum remove docker docker-common docker-selinux docker-engine
```

2. 安装一些依赖

```bash
yum install -y yum-utils device-mapper-persistent-data lvm2 wget
```

3. 配置docker的安装源

```bash
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
```

4. 将安装源替换成清华源

```bash
sed -i 's+download.docker.com+mirrors.tuna.tsinghua.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
```

5. 安装

```bash
yum makecache fast
yum install docker-ce
```
