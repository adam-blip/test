# https://github.com/lnstadrum/beatmup test on aarch64 chromebook 
activate crostini linux enironment under developer settings, open terminal:

sudo apt update
sudo apt install git python3-pip cmake libgl-dev -y

git clone https://github.com/lnstadrum/beatmup
cd beatmup
git submodule update --init --recursive
mkdir -p build && cd build

