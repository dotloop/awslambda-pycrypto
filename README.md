# AWS Lambda PyCrypto

For AWS Lambda you cannot compile PyCrypto locally and zip it.
You will get an error and the lambda won't run.

```
Crypto/Util/_counter.so: invalid ELF header
```

Fortunately someone has already compiled this library on an AWS EC2 instance so
that this will work.

https://github.com/Doerge/awslambda-pycrypto

To make sure we don't lose it the repo was forked.


## Replace PyCrypto

To replace PyCrypto once it has been installed in your virtual environment
do the following:

```
cd /path/of/virtualenv/lib/python2.7/site-packages/
rm -rf Crypto
rm -rf pycrypto-2.6.1.dist-info
git clone https://github.com/dotloop/awslambda-pycrypto.git
mv awslambda-pycrypto/Crypto ./Crypto
mv awslambda-pycrypto/pycrypto-2.6.1.dist-info ./pycrypto-2.6.1.dist-info
rm -rf awslambda-pycrypto
```
