#Centos：

##安装拓展库epel：
yum install epel-release

##centos6.5将python2.6升级为2.7

###1.安装额外的库
yum install zlib-devel openssl-devel sqlite-devel

安装gcc
yum install gcc


###2.下载python2.7.x源码

###3.安装2.7.x
cd Python-2.7.x 
./configure --prefix=/usr/local/python
make
make install

###4.替换python
rm /usr/bin/python /usr/bin/python2
ln -s /usr/local/python/bin/python2.7 /usr/bin/python2
ln -s /usr/bin/python2 /usr/bin/python

###5.修正yum
vim /usr/bin/yum
将第一行#!/usr/bin/python改为#!/usr/bin/python2.6


安装wget
yum install wget


##安装pip：

###1.安装setuptools:
https://pypi.python.org/pypi/setuptools
wget https://bootstrap.pypa.io/ez_setup.py -O - | python

###2.安装pip：
下载源码：https://pypi.python.org/pypi/pip#downloads
安装：python setup.py install

###3.建立软连接：（注意setuptools、pip安装的目录，默认在python安装目录下）
ln -s /usr/local/python/bin/easy_install /usr/bin/easy_install
ln -s /usr/local/python/bin/pip /usr/bin/pip

##更新gcc：
yum install gcc

##安装scrapy：

###1.安装libffi
源码安装：
wget ftp://sourceware.org/pub/libffi/libffi-3.2.1.tar.gz
tar -xzvf libffi-3.2.1.tar.gz
cd libffi-3.2.1
./configure
make
make install
// export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH
// export LD_LIBRARY_PATH=/usr/local/lib
export LD_LIBRARY_PATH=安装目录

未找到libffi.so.6的解决方法：
用find / -name libffi.so.6找到libffi.so.6的位置
复制到/usr/lib或/usr/lib64目录下
cp /usr/local/lib64/libffi.so.6 /usr/lib64/


yum安装：
yum install libffi libffi-devel

###2.安装cryptography
wget https://pypi.python.org/packages/source/c/cryptography/cryptography-0.4.tar.gz
tar -xzvf cryptography-0.4.tar.gz
cd cryptography-0.4
python setup.py build
python setup.py install

###3.安装lxml
依赖：
yum install libxslt-devel
源码安装：
下载：https://pypi.python.org/pypi/lxml/2.3/
安装：python setup.py install
pip安装：
pip install lxml

###4.安装Twisted
源码安装：
https://pypi.python.org/pypi上搜索源码包
比如：
http://pypi.python.org/packages/source/T/Twisted/Twisted-12.0.0.tar.bz2#md5=cf49a8676c21c50faf1b42b528049471

###5.安装scrapy
pip install scrapy
ln -s /usr/local/python/bin/scrapy /usr/bin/scrapy


安装service_identity（可能需要）
命令：	pip install service_identity

安装jieba分词：
pip install jieba


安装chardet


##安装截图模块：

yum install svn
yum install Xvfb

解决D-bus问题
dbus-uuidgen > /var/lib/dbus/machine-id

yum install CutyCapt



##参考：
http://www.tuicool.com/articles/URNVV3E
http://blog.chinaunix.net/xmlrpc.php?r=blog/article&uid=15588024&id=4145182
http://www.centoscn.com/image-text/install/2016/0216/6757.html
http://www.cszhi.com/20130305/cutycapt.html

chmod -R 777 directory 给目录下所有文件给予所有权限

chmod u+x file                　　　   给file的属主增加执行权限
$ chmod 751 file                　　　   给file的属主分配读、写、执行(7)的权限，给file的所在组分配读、执行(5)的权限，给其他用户分配执行(1)的权限
$ chmod u=rwx,g=rx,o=x file      上例的另一种形式
$ chmod =r file                 　　　　为所有用户分配读权限
$ chmod 444 file              　　　　 同上例
$ chmod a-wx,a+r   file   　　 　   同上例
$ chmod -R u+r directory       　   递归地给directory目录下所有文件和子目录的属主分配读的权限
$ chmod 4755                          　　设置用ID，给属主分配读、写和执行权限，给组和其他用户分配读、执行的权限。











