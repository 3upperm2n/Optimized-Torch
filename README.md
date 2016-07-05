[![Build Status](https://travis-ci.org/torch/distro.svg?branch=master)](https://travis-ci.org/torch/distro)

Self-contained Torch+MKLDNN installation
============
This is a intel torch version which integrated Torch with MKLDNN library.
MKLDNN library is a optimized  math library for deep neural network based IA, and it will be integrated in MKL,so be sure you have installed the lastest MKL

###Building
Before install, you should set the MKL path for cmake:

export CMAKE_INCLUDE_PATH=$CMAKE_INCLUDE_PATH:/opt/intel/mkl/include

export CMAKE_LIBRARY_PATH=$CMAKE_LIBRARY_PATH:/opt/intel/mkl/lib/intel64

Install dependencies. Uses `apt-get` on Ubuntu, which might require `sudo`. Uses `brew` on OSX.
```sh
curl -s https://raw.githubusercontent.com/torch/distro/master/install-deps | bash
```

Install this repo, which installs the torch distribution, with a lot of nice goodies.
```sh
git clone https://github.com/xhzhao/distro.git ./torch
cd ~/torch; ./install.sh
```
If you want to build torch with icc, use ./install_icc.sh instead of ./install.sh

If the submodule download process is broken due to network error, no worry,just retry the bash: ./install.sh, then the download process will continue.

The submodule of nn and torch7 is replaced with my own repo:https://github.com/xhzhao/nn, https://github.com/xhzhao/torch7.

By default Torch will install LuaJIT 2.1. If you want other options, you can use the command:
```sh
TORCH_LUA_VERSION=LUA51 ./install.sh
TORCH_LUA_VERSION=LUA52 ./install.sh
```

Now, everything should be installed. Either open a new shell, or source your profile via
```sh
. ~/.bashrc  # or: . ~/.zshrc
th -e "print 'I just installed Torch! Yesss.'"
```

Note: If you use a non-standard shell, you'll want to run this command
```sh
./install/bin/torch-activate
```

Tested on Ubuntu 14.04, CentOS/RHEL 6.3 and OSX


###Performance
To check the performance of Torch+MKLDNN, please use the benchmark:
https://github.com/xhzhao/Torch-MKLDNN-benchmark

To test Torch+MKLDNN on the imagenet dataset, refer to this link:  https://github.com/xhzhao/imagenet-CPU.torch
