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
* update timestamp using `ntpdate -b -u time.nist.gov`
* using latest [git client](http://stackoverflow.com/questions/21820715/how-to-install-latest-version-of-git-on-centos-6-x-7-x)
* PATH=/opt/centos/devtoolset-1.1/root/usr/bin:/usr/local/bin:/home/peter/depot_tools 

## checkout dart sdk
[github dart sdk](https://github.com/dart-lang/sdk)

````
   mkdir dart-sdk
   cd dart-sdk
   gclient config https://github.com/dart-lang/sdk.git
   gclient sync
   cd dart-sdk/sdk
   ./tools/build.py --mode release --arch x64 create_sdk
````

## Follow instruction build dart
[Build command](https://github.com/dart-lang/sdk/wiki/Building-Dart-on-CentOS,-Red-Hat,-Fedora-and-Amazon-Linux-AMI)


## for 1.6.x
replace `fwrite(....)` to `if(fwrite(...)){/* no op */}`
````
      vi runtime/bin/builtin_gen_snapshot.cc
````

download [analyzer_cli](https://github.com/dart-lang/analyzer_cli.git), copy to out/ReleaseX64/packages (src folder), and continue run 
`tools/build.py --mode=release --arch=x64 create_sdk` untile build pass  

checkedin executable `tools/sdks/linux/dart-sdk`  is not executable in centos, have to replace it with runnable one or remove linux folder to ignore it

## GCC 4.8.4
https://www.saintsouth.net/blog/update-libstdcpp-on-centos6/
