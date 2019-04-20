# Install OpenRAVE

We use the OpenRAVE core library for simulations.

- Official links: [[OpenRAVE](http://openrave.org/)]. [[OpenRAVE: Building and Installing page](http://openrave.org/docs/latest_stable/coreapihtml/installation.html)].

## Install OpenRAVE (Most modern Ubuntu, such as 14.04 or 16.04)

No official PPA, install from source. Note that you will be prompted for your password upon using `sudo`.

```bash
sudo apt install git
sudo apt install libboost-all-dev
sudo apt install libqt4-dev qt4-dev-tools libxml2-dev libode-dev
sudo apt install libsoqt4-dev libcoin80-dev
sudo apt install python-scipy  # For openravepy. Note that Xenial sympy is 0.7.6, see next line
pip install --upgrade --user sympy==0.7.1 # OpenRAVE ikfast needs sympy 0.7.1, https://github.com/rdiankov/openrave/pull/407
sudo apt install libcollada-dom2.4-dp-dev  # Open .zae files, only Ubuntu 16.04
cd  # go home
mkdir -p repos; cd repos  # create $HOME/repos if it doesn't exist; then, enter it
git clone --branch master https://github.com/rdiankov/openrave.git
cd openrave; mkdir build; cd build; cmake .. -DOPT_VIDEORECORDING=OFF  # Avoids AV errors
make -j$(nproc)
sudo make install; cd  # install and go home
```

Note that you may end up requiring over 2 GB of free space during the installation of `apt` dependencies. To avoid that, use the `--no-install-recommends` option as in:

`sudo apt install --no-install-recommends package`

Thus, `apt` would not try to install non-critical packages marked as *recommended* by the dependencies of OpenRAVE.

In case you run into `non-constant-expression cannot be narrowed from type 'double' to 'float' in initializer list [-Wc++11-narrowing]` errors (happened on OpenRAVE 0.15 and a Clang 6.0.0/7.0.0 compiler), reconfigure CMake with the following option:

`cmake .. -DOPENRAVE_IKFAST_FLOAT32=OFF`

## Install OpenRAVE with FCL (Confirmed for Ubuntu 15.04, 15.10, 16.10, 17.04)

```bash
sudo apt install libfcl-dev
cd $HOME/repos/openrave; mkdir build; cd build; cmake .. -DOPENRAVE_PLUGIN_FCLRAVE=ON
make -j$(nproc)
sudo make install; cd  # install and go home
```
For more references regarding FCL from source on other/older versions, refer to these issues: [#3](https://github.com/roboticslab-uc3m/installation-guides/issues/3), [#45](https://github.com/roboticslab-uc3m/installation-guides/issues/45).

## Install OpenRAVE (Ubuntu 12.04)

To install a precompiled version of OpenRAVE, type:

```bash
sudo add-apt-repository ppa:openrave/release
sudo apt-get update
sudo apt-get install openrave
```

## Install OpenRAVE (Windows)

Installers such as openrave-0.9.0-5cfc74-win32-vc100-setup are broken (break do to broken Boost 1.44 and Qt links, not to mention old VS version), so we go old-school.

References:
- http://robots.uc3m.es/index.php/OpenRAVE_R1457_Windows_Install
- https://www.cs.cmu.edu/~motionplanning/homework/hw1/hw1.html
- http://openrave.org/docs/latest_stable/coreapihtml/installation_windows.html
- http://sukhoy.public.iastate.edu/openrave/
- https://github.com/rdiankov/openrave

# Generate Databases

- https://github.com/roboticslab-uc3m/teo-openrave-models/tree/develop/scripts/python ([permalink](https://github.com/roboticslab-uc3m/teo-openrave-models/tree/0efd49e662495f8ca329ac0089fc37243ab7519c/scripts/python))

# External

## External Installation Tutorial/Script Links:
- https://github.com/crigroup/openrave-installation
   - Older by same user: [[ref1, trusty, see next link if still in trouble with FCL](http://fsuarez6.github.io/blog/openrave-trusty/)].
   - Older by same user: [[ref2, xenial](http://fsuarez6.github.io/blog/workstation-setup-xenial/)].
- [[ref3, xenial](http://www.aizac.info/installing-openrave0-9-on-ubuntu-trusty-14-04-64bit/)].

### External Tutorials
- https://scaron.info/teaching/getting-started-with-openrave.html
