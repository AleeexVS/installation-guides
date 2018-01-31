# Install XSENS
Download, compile and install XSENS YARP device from `icub-main` repository.
```bash
sudo apt install libgsl0-dev  # Seems to be hard dependency
cd  # go home
mkdir -p repos; cd repos  # make $HOME/repos if it doesn't exist; then, enter it
git clone https://github.com/robotology/icub-main
cd icub-main && mkdir build && cd build
cmake ..  -DENABLE_icubmod_xsensmtx=ON  # Configure the icub-main software
make -j$(nproc)  # compile
sudo make install
sudo ldconfig
```

Check installation:
```bash
yarpdev --list | grep xsensmtx
```

## View XSENS data

Run (may require `sudo`):
```bash
yarpdev --device inertial --subdevice xsensmtx --name /inertial
```

Data can be vizualized via classic `yarp read ... /inertial` or like in [teoTools.xml](https://github.com/roboticslab-uc3m/teo-configuration-files/blob/762ebe5079e05da38602e21e2feccd9901d8513d/share/teoTools/scripts/teoTools.xml#L74-L79).
