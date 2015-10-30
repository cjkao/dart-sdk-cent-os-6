DART for CENT OS 6.x
==================
64bit

## How to build?

* install [gcc dev compiler 4.7](http://superuser.com/questions/381160/how-to-install-gcc-4-7-x-4-8-x-on-centos)
    
````
    cd /etc/yum.repos.d
    wget http://people.centos.org/tru/devtools-1.1/devtools-1.1.repo 
    yum --enablerepo=testing-1.1-devtools-6 install devtoolset-1.1-gcc devtoolset-1.1-gcc-c++
````
* install [git 2.x](http://stackoverflow.com/questions/21820715/how-to-install-latest-version-of-git-on-centos-6-x-7-x)
````
    # yum remove git
    cd /usr/src
    wget https://www.kernel.org/pub/software/scm/git/git-2.0.4.tar.gz
    tar xzf git-2.0.4.tar.gz
    cd git-2.0.4
    make prefix=/usr/local/git all
    make prefix=/usr/local/git install
    echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/bashrc
    source /etc/bashrc
````
* install [python 2.7](https://github.com/h2oai/h2o-2/wiki/Installing-python-2.7-on-centos-6.3.-Follow-this-sequence-exactly-for-centos-machine-only)
        

## Setup Env 

* PATH=/opt/centos/devtoolset-1.1/root/usr/bin:/usr/local/bin:/home/peter/depot_tools 
