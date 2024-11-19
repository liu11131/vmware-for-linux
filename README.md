# vmware-for-linux

-- 安装vmmon和vmnet 补丁，参考https://www.cnblogs.com/wthuskyblog/p/16349940.htm

```
sudo apt-get update
sudo apt install -y build-essential git
VMWARE_VERSION=workstation-16.2.4
TMP_FOLDER=/mnt/data/tmp/patch-vmware
rm -fdr $TMP_FOLDER
mkdir -p $TMP_FOLDER
cd $TMP_FOLDER
git clone https://github.com/mkubecek/vmware-host-modules.git
cd $TMP_FOLDER/vmware-host-modules
git checkout $VMWARE_VERSION
git fetch
make
sudo make install
sudo rm /usr/lib/vmware/lib/libz.so.1/libz.so.1
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1 /usr/lib/vmware/lib/libz.so.1/libz.so.1
```
