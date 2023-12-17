## 源码安装

1. 下载
    国内下载地址：https://mirrors.huaweicloud.com/python/
2. 上次到linux目录

```shell
# 解压
tar -zxvf Python-2.7.9.tgz
# 
cd Python-2.7.9
```

3. 安装

```shell
# 配置
./configure --prefix=/usr/local/python-2.7.9
# 编译
make
# 安装
make install
```

4. 添加系统链接

```shell
ln -s /usr/local/python-2.7.9/bin/python /usr/bin/python
ln -s /usr/local/python-2.7.9/bin/pip /usr/bin/pip
```



```shell
tar -zxvf Python-3.9.13.tgz
cd Python-3.9.13/
./configure --prefix=/usr/local/python-3.9.13
make
make install
ln -s /usr/local/python-3.9.13/bin/python3.9 /usr/bin/python3.9
ln -s /usr/local/python-3.9.13/bin/pip3 /usr/bin/pip3.9
chmod 755 /usr/bin/python3.9
chmod 755 /usr/bin/pip3.9
```







pip源





1. 切换pip源



-  临时  

```bash
pip install markdown -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install orjson==3.5.2 -i http://mirrors.cloud.tencent.com/pypi/simple
pip install dataclasses==0.8 -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install jaeger-client==4.4.0 -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install jaeger-client==4.4.0 -i http://mirrors.cmrh.com/pypi/web/simple
```

-  长期  

```bash
# 金科源
pip config set global.index-url http://mirrors.cmrh.com/
pip config set global.index-url  http://mirrors.cmrh.com/pypi/web/simple
# 清华源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 或：
# 阿里源
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/
# 腾讯源
pip config set global.index-url http://mirrors.cloud.tencent.com/pypi/simple
# 豆瓣源
pip config set global.index-url http://pypi.douban.com/simple/
```



python-ldap安装不上



在https://www.lfd.uci.edu/~gohlke/pythonlibs/中下载对应的wheel文件



下载后安装



```bash
pip install wheel
pip install python_ldap-2.5.2-cp27-cp27m-win_amd64.whl  -- 路径
```



```bash
python3 -m pip install --upgrade pip setuptools wheel
python3 -m pip install --upgrade pip setuptools {file}
python3 -m pip install cryptography-3.4.7.tar.gz
```



```bash
python3 -m pip install --upgrade pip-21.1.3.tar.gz
# python3 -m pip install wheel-0.36.2.tar.gz
python3 -m pip install -U pip setuptools-57.4.0.tar.gz
python3 -m pip install RUST-0.1.1.tar.gz
python3 -m pip install cryptography-3.4.7.tar.gz
```

