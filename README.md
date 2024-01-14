# https://github.com/lnstadrum/beatmup test on aarch64 chromebook 
activate crostini linux enironment under developer settings, open terminal:

```
sudo apt update
sudo apt install git python3-pip cmake libgl-dev libglu-dev libegl-dev libgles-dev -y
```

```
git clone https://github.com/lnstadrum/beatmup
cd beatmup
git submodule update --init --recursive
mkdir -p build && cd build
```

```
sudo cmake -DUSE_EGL=ON -DGLES_VERSION=20 ..
sudo make X2 -j4
```

```
sudo make beatmup
cd ../python
sudo python3 setup.py bdist_wheel clean
sudo python3 -m pip install --no-index --find-links=dist beatmup
sudo python3 -c "import beatmup; beatmup.say_hi()"
```
