# Garlicoin
### Introduction
>   Garlicoin is hot out of the oven and ready to serve you with its buttery
>   goodness. Forked from LTC, this decentralized cryptocurrency with no new
>   technology (except it's ASIC resistant!!) will help you through the darkest
>   times in your life. This is the coin you never thought you needed, and you
>   probably don't.

-[/r/garlicoin](reddit.com/r/garlicoin)

Getting started
===============

In order to get started with Garlicoin, you first need to run a Garlicoin node.
This lets you access the Garlicoin network and do things like submit
transactions, solo mine, or host a pool.

## Running a node (garlicoind)

### Windows

There’s multiple ways to run a node on Windows but the easiest is to download
precompiled binaries. This only takes a couple of minutes to setup this way. If the latest precompiled binaries aren't available, skip to the **WSL method**. If neither of these methods works for you, you can try the **Docker method** as the last resort.

#### Precompiled binaries method
1.  Download and extract the [precompiled binaries](https://drive.google.com/open?id=19vGRyWKv-GDAbasAh60fNgbSVxFxBXcV). (updated Jan. 9 2018)
2.  Open Run and run `%appdata%`.
3.  Create a new folder called `Garlicoin` and open it.
4.  Create a new file called `garlicoin.conf` and open it with Notepad.
5.  Paste [this](https://pastebin.com/raw/BRGF9DTw), save and exit.
6.  Open the folder you extracted the binaries to and make a new file called
    `Start node.bat` and open it with Notepad.
7.  Paste this into it: `garlicoind -testnet -connect=52.89.91.13`.
8. Double click `Start node.bat` whenever you want to start a Garlicoin node
(also called garlicoind).

#### WSL method (64 bit Windows 10 only)
1. Install the Ubuntu distribution for [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
2. Open bash.
3. Run:
	* `sudo apt update`
	* `sudo apt install git software-properties-common`
	* `cd`
	* `git clone https://github.com/retosen/Garlicoin.git`
	* `sudo add-apt-repository ppa:bitcoin/bitcoin && sudo apt update`
	* `sudo apt-get install -y build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils libboost-all-dev libdb4.8-dev libdb4.8++-dev`
	* `cd Garlicoin`
	* `./autogen.sh && ./configure --without-gui --disable-tests && make && make install`
	* `cd ..`
	* `sudo mkdir .garlicoin && cd .garlicoin`
	* `nano garlicoin.conf`
4. Paste [this](https://pastebin.com/raw/BRGF9DTw), press ctrl+x, y, and enter to save and exit nano.
5. You can now run a Garlicoin node with: `garlicoind -testnet -connect=52.89.91.13`.

#### Docker method (64 bit Windows 10 Pro, Enterprise, or Education)
1. Install [Docker](https://docs.docker.com/engine/installation/).
2. Open command prompt.
3. Run:
	* `cd C:\`
	* `docker pull treetwig/garlicoin`
	* `mkdir garlicoin`
	* `cd garlicoin`
	* `notepad.exe garlicoin.conf`
4. Paste [this](https://pastebin.com/raw/BRGF9DTw) and save and exit Notepad
5. Run `docker run -it -v C:\garlicoin:/root/.garlicoin -p 127.0.0.1:42070:42070 treetwig/garlicoin`
6. The terminal should now change to look something like:
	> root@[numbers and letters]:/#
7. Run `garlicoind -testnet -connect=52.89.91.13 &`
8. The Garlicoin node should now be accessible to you on rpc port 42070 in both the Docker container and your host computer.


#### Compiling the Windows binaries yourself
Follow [these](https://github.com/retosen/Garlicoin/blob/master/doc/build-windows.md) steps.
