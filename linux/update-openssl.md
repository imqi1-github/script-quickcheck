## OpenSSL版本过低，需升级

NodeJS、NPM、Docsify等运行时报错：node: relocation error: /lib64/libnode.so.93: symbol FIPS_selftest, version OPENSSL_1_1_0g not defined in file libcrypto.so.1.1 with link time reference
原因：NodeJS版本太高，与系统OpenSSL版本不对应。

解决方法：

将 OpenSSL 升级到 1.1.1 版本：

1. 依赖包

安装编译 OpenSSL 所需的包，包括 gcc、make、perl 和 zlib-devel。可以通过运行以下命令完成：

```bash
yum install -y gcc make perl zlib-devel
```

2. 安装包下载

下载 OpenSSL 1.1.1 的源码包，可以从 OpenSSL 官网下载（https://www.openssl.org/source/openssl-1.1.1.tar.gz）或使用以下命令下载：

```bash
wget https://www.openssl.org/source/openssl-1.1.1.tar.gz
```

3. 解压

解压源码包并进入解压后的目录：

```bash
tar -zxvf openssl-1.1.1.tar.gz
cd openssl-1.1.1
```

4.初始化并编译、安装

运行以下命令编译 OpenSSL：

```bash
./config --prefix=/opt/openssl-1.1.1
make
make install
```

5. 做软连接

```bash
mv /usr/bin/openssl /usr/bin/openssl_20230525bak
mv /usr/lib64/openssl /usr/lib64/openssl_20230525bak
```

然后将新安装的OpenSSL做软连接到这个路径

```bash
ln -s /opt/openssl-1.1.1/bin/openssl /usr/bin/openssl
```

执行以下命令检查 OpenSSL 版本：

```bash
openssl version
```
