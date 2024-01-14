# https://github.com/lnstadrum/beatmup test on aarch64 chromebook 
activate crostini linux enironment under developer settings, open terminal:

```
sudo apt update
sudo apt install wget git python3-pip cmake libgl-dev libglu-dev libegl-dev libgles-dev libdrm-dev libgbm-dev -y
```

```
git clone https://github.com/lnstadrum/beatmup
cd beatmup
git submodule update --init --recursive
mkdir -p build && cd build
```

```
sudo cmake -DUSE_EGL_DRM=ON -DGLES_VERSION=20 ..
sudo make X2 -j4
```

```
sudo make beatmup -j4
cd ../python
sudo python3 setup.py bdist_wheel clean
sudo python3 -m pip install --no-index --find-links=dist beatmup --break-system-packages
sudo python3 -c "import beatmup; beatmup.say_hi()"
```

```
sudo pip3 install opencv-python --break-system-packages
cd examples
wget https://github.com/adam-blip/test/raw/master/star.bmp
sudo python3 x2_superresolution.py star.bmp
```
