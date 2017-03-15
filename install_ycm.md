# Install YCM

We use YCM to benefit from additional CMake modules and superbuild support. The source code is hosted on [GitHub](https://github.com/robotology/ycm). Due to its nature, you may want to install it on your system (as a so-called hard dependency) or lazy-load on demand (soft dependency).

## Install YCM (Ubuntu) - hard dependency

Note that you will be prompted for your password upon using `sudo`. Type:

```bash
cd                                               # go home
mkdir -p repos; cd repos                         # make $HOME/repos if it doesn't exist; then, enter it
git clone https://github.com/robotology/ycm.git  # clone repository
cd ycm; mkdir build; cd build; cmake ..          # configure
sudo make install; cd                            # install and return home
```

## Include YCM in CMake project - soft dependency

CMake-based projects may bootstrap YCM so that its sources are downloaded on demand - it's up to the developers to reflect this in the documentation. Under these assumptions, you should not worry about the previous installation step as everything would land in your project's `<build-tree>/install` directory by default. However, you may want to avoid this process (and the subsequent need for Internet connection) by installing YCM in your system paths - in this respect, please refer to the previous section. Additionally, it must be noted that bootstrapping YCM itself as well as downloading any remote package integrated in the superbuild requires that an appropriate VCS client is installed on the system. Usually, these projects are Git-based and all you need to do is to install `git` (we assume you did this already):

```bash
sudo apt-get install git
```

## Using YCM on Ubuntu 12.04

YCM requires CMake 2.8.9 or later, which means that you need to compile or backport CMake on Ubuntu precise (12.04) releases. You may either [upgrade to 2.8.11.2](install_cmake.md#ubuntu-1204-backports) or [compile 2.8.9 with OpenSSL support](install_cmake.md#openssl-support).
