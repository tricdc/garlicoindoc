# Garlicoin
this documentation written by snake 🐍
### Introduction
>   Garlicoin is hot out of the oven and ready to serve you with its buttery
>   goodness. Forked from LTC, this decentralized cryptocurrency with no new
>   technology (except it's ASIC resistant!!) will help you through the darkest
>   times in your life. This is the coin you never thought you needed, and you
>   probably don't.

-[/r/garlicoin](reddit.com/r/garlicoin)

Getting started
===============

In order to get started with Garlicoin, you first need to run a Garlicoin node or **[setup a web wallet](http://breadbox.xyz)**. **Word of caution:** setting up a wallet locally rather than with the web wallet is **safer**. This lets you access the Garlicoin network and do things like submit
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


#### Compiling the Windows binaries yourself with WSL
Follow [these](https://github.com/retosen/Garlicoin/blob/master/doc/build-windows.md) steps.
[More info](https://github.com/BrennanMcDonald/garlicoin-bible/blob/master/Windows/Build_TestNet.md)

---

### macOS

#### Building
There is a great guide [here](https://github.com/BrennanMcDonald/garlicoin-bible/blob/master/Mac/Build_TestNet.md).

---

### Linux

#### Building

There is a great guide [here](https://github.com/BrennanMcDonald/garlicoin-bible/blob/master/Linux/Build_TestNet.md).

---

## Creating a wallet
You have two options at the moment for creating a wallet. (Note: running garlicoind creates a default wallet)

1. Create one locally (safer)
2. Use a web wallet (easier)

### Creating a wallet locally
1. Start your garlicoind node.
2. Open another terminal/command prompt window
3. Run the command `garlicoin-cli -testnet getnewaddress [yourwalletname]`
	* It's likely that [yourwalletname] will be "" as this is the default name that is generated when first running garlicoind.
4. The console will output your new address.

### Creating a web wallet
As of now the only web wallet is [http://breadbox.xyz](http://breadbox.xyz). It doesn't require any node to run or interact with and supports 2FA.

---

## Obtaining Garlicoins (GRLC)
Garlicoins can be obtained either from mining them or by buying them from an exchange. As of now, there is no current way to buy Garlicoins on an exchange. This will change in the future.

---

## Mining Garlicoins ⛏️

Mining Garlicoin can be done with a CPU or GPU. Mining Garlicoin uses the scrypt-n algorithm which is **ASIC resistant** meaning that mining will be easier for more people to do. Mining can either be done in a pool with other miners, or by yourself. Pool mining is easier to setup as it doesn't require a node to be running on your computer. If your hardware isn't very powerful (most CPUs) you should pool mine.

### Pool Mining (GPUs)
#### Windows
##### AMD
The current miner used for AMD GPU is [YACMiner](https://github.com/Thirtybird/YACMiner). You can download precompiled Windows binaries [here](https://drive.google.com/open?id=1T5P2sm0iYFwGU1kViK7yyKVKsMsULSVg).

To mine to a pool:

* Edit the yacminer command in "mine.bat"
* Change `stratum+tcp://127.0.0.1:3333` to whatever stratum address the pool you are mining to provides you.
* Change `mzJeLWYDTwimZuV9CiYKVH5h2QJ4uRXTj6` to your Garlicoin address
* Open "mine.bat"

You now should be mining.