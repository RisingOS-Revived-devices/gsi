<p align="center">
<img src="https://github.com/RisingOS-OSS/android/blob/fifteen/risingOS_banner.png?raw=true">
</p>


RisingOS Revived GSI
------------------


Getting Started
---------------


You'll need to get familiar with [Git and Repo](https://source.android.com/source/using-repo.html) as well as [How to build a GSI](https://github.com/phhusson/treble_experimentations/wiki/How-to-build-a-GSI%3F).



Building the GSI
---------------

**Create the directory**
```bash
mkdir rising
cd rising
```

**To initialize your local repository using the Infinity source, use a command like this:**

```bash
repo init -u https://github.com/RisingOS-Revived/android -b sixteen --git-lfs --depth=1
```
**Sync up with this command:**
```bash
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j16
```

---------------
**clone all repo** 

```bash
git clone https://github.com/TrebleDroid/vendor_interfaces -b android-15.0 vendor/interfaces

git clone https://github.com/Doze-off/device_phh_treble -b android-16 device/phh/treble

git clone https://github.com/TrebleDroid/treble_app -b master treble_app

git clone https://github.com/AndyCGYan/android_packages_apps_QcRilAm -b master packages/apps/QcRilAm

git clone https://github.com/TrebleDroid/vendor_hardware_overlay -b pie vendor/hardware_overlay

git clone https://android.googlesource.com/platform/prebuilts/vndk/v28  prebuilts/vndk/v28

git clone https://android.googlesource.com/platform/prebuilts/vndk/v29 prebuilts/vndk/v29

git clone https://github.com/ponces/treble_adapter -b master treble_adapter

git clone https://github.com/RisingOS-Revived-devices/treble-patches -b sizteen patches
```

---------------
Move the **apply-patches.sh** script and **patches-rising** inside the patches folder to the **main folder** with command:
```bash
cp -r patches/* .
```

**Use the command:**
```bash
bash apply-patches.sh .
```
**Note:** if some patches fail, you have to apply them manually


---------------
Then start building

**Compilation: Follow the commands**
```bash
source build/envsetup.sh
lunch rising_gsi-userdebug
make systemimage -j16
```
**Compress:**
```bash
xz -9 -T0 -v -z out/target/product/tdgsi_arm64_ab/system.img
```
