# Debian

Python 2.7.16 - March 4, 2019
```

sudo useradd pyspace
sudo apt-get install zlib1g-dev
wget https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz
tar xvfz Python-2.7.16
cd Python-2.7.16
./configure --with-prefix="/home/pyspace/.py"
make
sudo make install

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
PYTHONPATH="/home/pyspace/py/packages" python setup.py install
cd ..
cd greenlet-0.4.17
PYTHONPATH="/home/pyspace/py/packages" python setup.py install
cd ..

git clone git@github.com:JFOXLEY/gevent-1.5.0-patch.git
patch gevent-1.5.0/src/gevent/_socket3.py < gevent-1.5.0-patch/_socket3.py

cd gevent-1.5.0
PYTHONPATH="/home/pyspace/py/packages" python setup.py install

```