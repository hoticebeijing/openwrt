本源码生成的固件禁止使用在任何非法、商业用途！

1. 安装编译Python需要的环境

yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel

安装pip
#运行这个命令添加epel扩展源
yum -y install epel-release
#安装pip
yum install python-pip

2. 用wget下载python3的源码包
cd /usr/local/src/
wget https://www.python.org/ftp/python/3.8.2/Python-3.8.2.tar.xz
编译python3源码包

#解压
xz -d Python-3.8.2.tar.xz
tar -xf Python-3.8.2.tar
#进入解压后的目录，依次执行下面命令进行手动编译
cd Py*
./configure prefix=/usr/local/python3
make && make install

python3安装完毕

#添加python3的软链接
rm /usr/bin/python
ln -s /usr/bin/python /usr/local/python3/bin/python3


3. git clone https://github.com/hoticebeijing/openwrt.git    
4. adduser op
5. password op 
6. chmod 777 ./openwrt op
7. cd openwrt
8. ./scripts/feeds clean

9   ./scripts/feeds update -a
10 ./scripts/feeds install -a
   
11. make menuconfig 
   
12 make -j8 download v=s 下载dl库(可增加99%编译成功率。需全程科学上网）
   
   编译完成后输出路径：
   固件：/lede/bin/targets

5. 最后选好你要的路由，输入 make -j1 V=s （-j1 后面是线程数。第一次编译推荐用单线程）即可开始编译你要的固件了。

你可以自由使用，但源码编译二次发布请注明我的 GitHub 仓库链接。谢谢合作！
 
 -----------------------------------------------------
 
My app source code: https://github.com/Lienol/openwrt-package

This is the buildsystem for the OpenWrt Linux distribution.

To build your own firmware you need a Linux, BSD or MacOSX system (case
sensitive filesystem required). Cygwin is unsupported because of the lack
of a case sensitive file system.

You need gcc, binutils, bzip2, flex, python, perl, make, find, grep, diff,
unzip, gawk, getopt, subversion, libz-dev and libc headers installed.

1. Run "./scripts/feeds update -a" to obtain all the latest package definitions
defined in feeds.conf / feeds.conf.default

2. Run "./scripts/feeds install -a" to install symlinks for all obtained
packages into package/feeds/

3. Run "make menuconfig" to select your preferred configuration for the
toolchain, target system & firmware packages.

4. Run "make" to build your firmware. This will download all sources, build
the cross-compile toolchain and then cross-compile the Linux kernel & all
chosen applications for your target system.

Sunshine!
	Your OpenWrt Community
	http://www.openwrt.org


