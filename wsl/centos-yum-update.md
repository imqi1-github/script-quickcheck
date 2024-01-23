## CentOS 8 yum 更新时提示 Error: Failed to download metadata for repo ‘AppStream’: Cannot prepare internal mirrorlist: No URLs in mirrorlist 的解决方法

CentOS Linux 8 已于 2021 年 12 月 31 日到达生命的尽头(EOL)。这意味着 CentOS 8 将不再从官方 CentOS 项目获得开发资源。在 2021 年 12月 31 日之后，如果需要更新你的 CentOS，需要将镜像更改到 vault.centos.org，在那里它们将被永久存档。

```bash
# 进入 /etc/yum.repos.d/ 目录
cd /etc/yum.repos.d/

# 运行以下命令
sudo sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

# 重新运行 yum 命令
sudo yum update -y
```
