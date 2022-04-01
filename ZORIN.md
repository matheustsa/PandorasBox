ZORIN OS GUIDES
======================================

### Install TP-LINK TL-WN725N wifi adapter.

I had a damn job trying to get this adapter to work until I found [this answer](https://www.youtube.com/user/homergfunk) on askubuntu, hope it helps you too!

🚀 Installation
---------------

Simply enter following commands in your terminal :

```bash
sudo apt update
sudo apt install git 
git clone https://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo -i
echo “blacklist r8188eu”  >>  /etc/modprobe.d/blacklist.conf
modprobe -r r8188eu
exit
```

Remove and reinsert your USB wireless adapter and check if it finds any network.
At each newer kernel version update, after the requested restart, please do:

```bash
cd rtl8188eu
make clean
git pull
make
sudo make install
```
---------------

