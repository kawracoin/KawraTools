# Kawra (KAWRA)

**Kawra** is a SHA-256 Proof-of-Work cryptocurrency built on Bitcoin Core 25.0. Designed with simplicity, fairness, and decentralization in mind, Kawra has a limited fixed supply and predictable emission schedule.

This repository contains the full Kawra blockchain node and wallet source code.

---

## 🪙 Coin Properties

| Property                  | Value                       |
|---------------------------|-----------------------------|
| **Coin Name**             | Kawra                       |
| **Ticker**                | KAWRA                       |
| **Unit**                  | ka                          |
| **Algorithm**             | SHA-256 (Proof-of-Work)     |
| **Block Time**            | 5 minutes                   |
| **Block Reward**          | 10 KAWRA                    |
| **Halving Interval**      | 200,000 blocks              |
| **Max Supply**            | 4,000,000 KAWRA             |
| **Public Address Prefix** | K                           |
| **RPC Port**              | 23917                       |
| **P2P Port**              | 23918                       |
| **Dev Reward**            | ❌ None                     |
| **Difficulty Adjustment** | Every 2 hours (~24 blocks)  |
| **Source Base**           | Bitcoin Core 25.0           |
| **License**               | MIT                         |

---

## ⚙️ Sample Configuration (`kawra.conf`)

Place this in: `~/.kawra/kawra.conf`

```ini
rpcuser=rpc_kawra
rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2
rpcbind=127.0.0.1
rpcallowip=127.0.0.1
listen=1
server=1
txindex=1
daemon=1
```

---

## 🧱 Compile Kawra Wallet from Source

### 🖥️ Linux Wallet Build (Ubuntu Server 22.04)

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install make automake cmake curl g++-multilib libtool binutils-gold \
bsdmainutils pkg-config python3 patch bison -y

cd ~/
mkdir source_code
cd source_code
wget "https://github.com/kawracoin/KawraTools/raw/main/kawra-source-code.tar.gz" -O kawra-source-code.tar.gz
tar -xzvf kawra-source-code.tar.gz
```

#### 64-bit Build
```bash
PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=x86_64-pc-linux-gnu
cd ..
./autogen.sh
CONFIG_SITE=$PWD/depends/x86_64-pc-linux-gnu/share/config.site ./configure --prefix=/
make
```

#### Optional Cleanup
```bash
make clean
```

#### 32-bit Build
```bash
cd depends
make HOST=i686-pc-linux-gnu
cd ..
./autogen.sh
CONFIG_SITE=$PWD/depends/i686-pc-linux-gnu/share/config.site ./configure --prefix=/
make
```

---

### 🪟 Windows Wallet Build (on Ubuntu Server 22.04)

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install make automake cmake curl g++-multilib libtool binutils-gold \
bsdmainutils pkg-config python3 patch bison -y

cd ~/
mkdir source_code
cd source_code
wget "https://github.com/kawracoin/KawraTools/raw/main/kawra-source-code.tar.gz" -O kawra-source-code.tar.gz
tar -xzvf kawra-source-code.tar.gz

sudo apt-get install g++-mingw-w64-x86-64 -y
sudo update-alternatives --set x86_64-w64-mingw32-g++ /usr/bin/x86_64-w64-mingw32-g++-posix

cd depends
make HOST=x86_64-w64-mingw32
cd ..
./autogen.sh
CONFIG_SITE=$PWD/depends/x86_64-w64-mingw32/share/config.site ./configure --prefix=/
make
```

---

## 🚀 Running Kawra

```bash
./src/kawrad -daemon
./src/kawra-cli getnewaddress
./src/kawra-cli getbalance
./src/kawra-cli sendtoaddress <address> <amount>
```

---

## 🌐 Network

- **Main Node**: `node1.kawra.org`
- **Block Explorer**: [https://explorer.kawra.org](https://explorer.kawra.org)
- **Mining Pool**: [http://pool.kawra.org](http://pool.kawra.org)

---

## ✅ Testnet

```bash
./src/kawrad -testnet -daemon
```

---

## 🤝 Contributing

We welcome community contributions. Fork the repo, create a branch, and submit a pull request.  
See [`CONTRIBUTING.md`](CONTRIBUTING.md) for details.

---

## 🛡️ License

Kawra is open-source software licensed under the [MIT License](COPYING).
