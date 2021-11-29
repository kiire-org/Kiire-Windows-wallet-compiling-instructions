# Kiire-Windows-wallet-compiling-instructions
Compile a wallet for Microsoft Windows on Ubuntu Server

**Update your Ubuntu server with the following command:**

sudo apt-get update && sudo apt-get upgrade -y

**Install the required dependencies with the following command:**

sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 curl libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libgmp3-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev unzip doxygen cmake nsis wine-stable wine64 bc -y

**Install the repository ppa:bitcoin/bitcoin with the following command:**

sudo add-apt-repository ppa:bitcoin/bitcoin

**Confirm the installation of the repository by pressing on the enter key.**

**Install Berkeley DB with the following command:**

sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y

**Create your source code directory with the following commands:**

cd ~/
mkdir source_code
cd source_code

**Download the source code of your coin with the following command:**

wget "https://github.com/kiire-org/Kiire-Source-code/raw/main/kiire-source.tar.gz" -O kiire-source.tar.gz

**Type the following command to extract the tar file:**

tar -xzvf kiire-source.tar.gz

**64-bit**

**Install the required dependencies with the following command:**

sudo apt-get install g++-mingw-w64-x86-64 -y

**Set the default x86_64-w64-mingw32-g++ compiler option to posix with the following command:**

sudo update-alternatives --set x86_64-w64-mingw32-g++ /usr/bin/x86_64-w64-mingw32-g++-posix

**Build x86_64-w64-mingw32 with the following commands:**

PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=x86_64-w64-mingw32
cd ..

**Type the following commands to compile your 64 bit wallet for Microsoft Windows.**

./autogen.sh
CONFIG_SITE=$PWD/depends/x86_64-w64-mingw32/share/config.site ./configure --prefix=/
make

**32-bit**

**Type the following command to clean your source code:**

make clean

**Install the required dependencies with the following command:**

sudo apt-get install g++-mingw-w64-i686 mingw-w64-i686-dev -y

**Set the default i686-w64-mingw32-gcc and i686-w64-mingw32-g++ compiler option to posix with the following commands.**

sudo update-alternatives --set i686-w64-mingw32-gcc /usr/bin/i686-w64-mingw32-gcc-posix

sudo update-alternatives --set i686-w64-mingw32-g++ /usr/bin/i686-w64-mingw32-g++-posix

**Build i686-w64-mingw32 with the following commands:**

PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=i686-w64-mingw32
cd ..

**Type the following commands to compile your 32 bit wallet for Microsoft Windows.**

./autogen.sh
CONFIG_SITE=$PWD/depends/i686-w64-mingw32/share/config.site ./configure --prefix=/
make

**The compiled wallet for Microsoft Windows is located in the directory src/qt, the tools are located in the directory src.**
