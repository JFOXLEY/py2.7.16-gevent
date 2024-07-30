# Debian

Python 2.7.16 - March 4, 2019
```

sudo useradd pyspace -d /home/pyspace -m -p CRYPTO
mkdir /home/pyspace/.py
sudo apt-get install zlib1g-dev 
wget https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz
mv Python-2.7.16.tgz Python-2.7.16.tar.gz
tar zxvf Python-2.7.16.tar.gz
cd Python-2.7.16
./configure --prefix="/home/pyspace/.py/"
make
sudo make install
sudo chown -R pyspace:pyspace /home/pyspace/.py/

su pyspace
mkdir py && cd py
mkdir packages
```
Now copy the PYPI repository files in to the py folder

```
tar zxvf setuptools.py2716.tar.gz
tar xvzf gevent-1.5.0.tar.gz
tar xvzf greenlet-0.4.17.tar.gz
cd setuptools-39.2.0/
PYTHONPATH="/home/pyspace/py/packages" /home/pyspace/.py/bin/python setup.py install
cd ..
cd greenlet-0.4.17
PYTHONPATH="/home/pyspace/py/packages" /home/pyspace/.py/bin/python setup.py install
cd ..

wget https://github.com/JFOXLEY/gevent-1.5.0-patch/archive/refs/tags/release.tar.gz
tar zvxf release.tar.gz
patch gevent-1.5.0/src/gevent/_socket3.py < gevent-1.5.0-patch-release/_socket3.patch

cd gevent-1.5.0
PYTHONPATH="/home/pyspace/py/packages" /home/pyspace/.py/bin/python setup.py install

```