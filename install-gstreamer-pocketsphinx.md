# Install gstreamer with pocketsphinx

We use `gstreamer` with `pocketsphinx` within speech recognition.

## Install gstreamer

```bash
sudo apt install libgstreamer1.0-dev
sudo apt install libgstreamer-plugins-base1.0-dev
```

## Install pocketsphinx dependencies

To compile `pocketsphinx` from source, `sphinxbase` is a dependency.

- [Install sphinxbase](install-sphinxbase.md)

## Install pocketsphinx

```bash
sudo apt install autoconf libtool
cd  # go home
mkdir -p repos; cd repos  # create $HOME/repos if it doesn't exist; then, enter it
git clone https://github.com/cmusphinx/pocketsphinx
cd pocketsphinx
./autogen.sh
./configure
make -j$(nproc)  # compile
sudo make install # install
```

## Configure gstreamer with pocketsphinx

We need to configure the path to look for shared libaries:

```bash
echo "export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/usr/local/lib/gstreamer-1.0" >> ~/.bashrc
```

## Verify gstreamer with pocketsphinx

To verify that GStreamer can find the plugin. You should get a large amount of output, ending with something like this:

```bash
gst-inspect-1.0 pocketsphinx

decoder             : The underlying decoder
                       flags: readable
                       Boxed pointer of type "PSDecoder"
```

To test that all is running ok:

```bash
pocketsphinx_continuous -inmic yes
```

## Troubleshooting gstreamer with pocketsphinx

Most importantly, follow steps in correct order: first [gstreamer](#install-gstreamer), then [pocketsphinx](#install-pocketsphinx), and finally configure. If you install `pocketsphinx` without `gstreamer`, you'll end up having to install `gstreamer` first, then re-`.configure`  `pocketsphinx`, compile and install again.

Some tutorials also recommend:
```bash
echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib" >> ~/.bashrc
echo "export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig" >> ~/.bashrc
```

As well as:
```bash
sudo modprobe snd_pcm_oss # Depends on your sound system
```

## References

- https://cmusphinx.github.io/wiki/gstreamer/
