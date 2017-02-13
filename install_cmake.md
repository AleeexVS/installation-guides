# Install CMake

We use CMake for project generating.

Official download page: [link](https://cmake.org/download/)

## Install CMake (Ubuntu)

Installing CMake on Ubuntu is quite straightforward. Note that you will be prompted for your password upon using `sudo`. Type:

```bash
sudo apt-get install cmake
sudo apt-get install cmake-curses-gui  # Recommended, as it contains ccmake.
```

## Install CMake (Debian 6.0.10): v2.8.9

Make sure you have backports set up as indicated on [teo_body_install_on_debian_6.md](https://github.com/roboticslab-uc3m/teo-body/blob/develop/doc/teo_body_install_on_debian_6.md).

Then run the following lines from a terminal. Note that you will be prompted for your password upon using `sudo`.

```bash
sudo apt-get update
sudo apt-get install -t squeeze-backports cmake cmake-curses-gui
```
