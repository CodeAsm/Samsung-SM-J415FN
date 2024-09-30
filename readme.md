# Samsung SM-J415FN (Galaxy J4+)

These are my notes on getting another rom on this phone. Not my primairy phone, but i hope I can make use of this and learn how to do so maybe on my primairy.

## Notes
btw, im an Arch user.

### Get odin and adb

enable devoper mode, probably unlock the OEM bootlaoder thing and allow USB debugging for adb (both cool and maybe not all needed at the same time). After OEM unlock, you need dev mode again, and now be a great time for USB debug.

```sh
yay odin4-cli android-sdk-platform-tools
```

Create a new file if it doesn't exist already: `/etc/udev/rules.d/51-android.rules`

with the following contents (on Arch, ubuntu noobs use plugdev)
```sh
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666", TAG+="uaccess"
```
to load?
```sh
udevadm control --reload
```

after usb debug allow, check this out:
```sh
adb devices
```
so cool
 you can upload apk now and such. many wow.

### odin4 download mode
for download mode, google the keycombo (``Volume Down + Volume Up + Power button`` in my case) or

```adb
adb reboot download
```
now for example, run the "safe" command"
```odin
odin4 -l
```
it may spit out:
```code
/dev/bus/usb/003/025
```

### Flash TWRP

in Download mode, type the following, with the location of your TWRP file in mind. Any errors might appear very small in the upper left side of your phones lcd.

```sh
odin4 -a ../TWRP/twrp-3.7.0_9-0-j4primelte.img.tar.md5
```


### How to boot into TWRP recovery on a Samsung Galaxy device

Switch off your device.
Press and hold ``Home + Power + Volume Up`` buttons for a few seconds and as soon as you see your device’ logo on-screen, release three buttons altogether. Your device will boot into TWRP recovery.

### Backup?

### Locked, Only official 

basicly im locked out? leave phone on for 7 days?
https://xdaforums.com/t/guide-17-06-2019-rmm-kg-bypass-root-install-twrp-on-exynos-samsung-after-2018.3747535/

https://xdaforums.com/t/guide-17-06-2019-rmm-kg-bypass-root-install-twrp-on-exynos-samsung-after-2018.3747535/

I tried:
https://xdaforums.com/t/unofficial-12-1-lineageos-19-1-for-galaxy-j4-j4primelte.4517067/
especially:
https://xdaforums.com/t/unofficial-12-1-lineageos-19-1-for-galaxy-j4-j4primelte.4517067/#post-87864085

https://twrp.me/samsung/samsunggalaxyj4plus.html

Well, that or whatever fixed my issue. I had amoung other things, flashed the stock os and set back my clock/date a year before the last update (somewhere november 2019). And then odin4 -a twrp worked as a charm.

### Flash Lineageos

Well, after i got TWRP working, it was simple, i made a backup on my SD and then, wiped (full) data and lineageos installed easy.
(cleaning Dalvik/cache also smart.)

## Dalvik/Cache
I dint knew, but after you flash a new rom, just clean dalvik/cache.
I cant find the stackoverflow that explained it so nice, but https://xdaforums.com/t/what-does-wiping-dalvik-cache-do.1752390/ does a bit.

basicly when you run apps (or the system does) the dalvik cache cashes stuff for them, so they may run faster next time. when swapping roms, all these chached apps nomore match whats on your new rom. so better just wipe the cache dalvik stuff, so a new collection is made during runtime. something with hashes too maybe.

## General Information
- Model: Samsung SM-J415FN
- Series: Galaxy J4+

### Specifications
- **Display:** 6.0 inches, 720 x 1480 pixels
- **Processor:** Quad-core 1.4 GHz Cortex-A53
- **RAM:** 2GB / 3GB
- **Storage:** 16GB / 32GB
- **Battery:** 3300 mAh
- **OS:** Android 8.1 (Oreo), upgradable to Android 9.0 (Pie)

## Development Notes

Guess what, the stock os and lineageos is just 32bits :(
so we need our own 64bits os maybe

https://xdaforums.com/t/guide-how-to-building-lineageos-for-an-unsupported-device.4419263/
https://medium.com/@daltonfury42/building-lineageos-for-your-device-a7d26ab50549
https://wiki.lineageos.org/devices/gts28vewifi/build/
https://wiki.lineageos.org/devices/kenzo/build/

for these we need the source tree and device tree:

- [Device tree samsung msm8917](https://github.com/msm8917-dev/android_device_samsung_msm8917-common)
- [kernel source samsung msm8917](https://github.com/msm8917-dev/android_kernel_samsung_msm8917)

Alternative, ased on (https://xdaforums.com/t/rom-unofficial-10-lineageos-17-1-for-galaxy-j4-j4primelte.4057939/):

- [Device tree](https://github.com/MacTavishAO/android_device_samsung_j4primelte)
- [Common Device tree](https://github.com/MacTavishAO/android_device_samsung_msm8917-common)
- [Vendor blobs](https://github.com/MacTavishAO/proprietary_vendor_samsung)
- [Kernel source](https://github.com/MacTavishAO/android_kernel_samsung_msm8917)

some 64bit? (compare with above, find original samsung?)
- [havoc uses this?](https://github.com/geckyn/android_kernel_samsung_msm8917_64)
- [havoc](https://github.com/Havoc-OS)
- [Havoc OS on XDA](https://xdaforums.com/t/rom-arm64-10-0-havoc-os-3-6-for-galaxy-j4-unofficial.4086831/)

### Useful Links
- [Official Samsung Support](https://www.samsung.com/support/)
- [XDA Developers Forum](https://forum.xda-developers.com/)
- [Lineageos 19.1 for Samsung](https://xdaforums.com/t/unofficial-12-1-lineageos-19-1-for-galaxy-j4-j4primelte.4517067)
- [TWRP](https://twrp.me/samsung/samsunggalaxyj4plus.html)
- [Odin for Arch Linux](https://aur.archlinux.org/packages/odin4-cli)
- [Pokemon go on Lineagesos](https://digiex.net/threads/play-pokemon-go-with-a-custom-rom-or-root-lineageos-19-20-android-12-13-how-to.15624/)

## Official source

Found Samsung does still provide the sources for this phone officially. if not anymore, I got them, and they are in this repo folder "official". In case you dont trust me, or another source, check them yourself and tripple ask yourself why the sha256 matches or not. (if they do match, from another source, my asumption is, you got the real deal)

The sha256 for the zip should be:
``dd67a9a3d7500a8b02f78d97e3d03297ceec3353adea9516386c5bd7123f25e9``

and if you prever md5 ``25a77d767d2b78d45a7ce1a821759f7e``

sourced it from https://opensource.samsung.com/uploadList


``SM-J415FN, J415FNXXS6BVJ1, SM-J415FN_CIS_PP_Opensource.zip``

### Git doesnt support large files (unless lfs)

where is SM-J415FN_CIS_PP_Opensource.zip ? 
ive split the archive, run this, then check hash:
```sh
cat x* > SM-J415FN_CIS_PP_Opensource.zip
sha256sum SM-J415FN_CIS_PP_Opensource.zip
```

ive used the following if your curious:
```sh
split --bytes=50M SM-J415FN_CIS_PP_Opensource.zip
```

### Flash TWRP

### Backup?

### Flash Lineageos

## General Information
- Model: Samsung SM-J415FN
- Series: Galaxy J4+

### Specifications
- **Display:** 6.0 inches, 720 x 1480 pixels
- **Processor:** Quad-core 1.4 GHz Cortex-A53
- **RAM:** 2GB / 3GB
- **Storage:** 16GB / 32GB
- **Battery:** 3300 mAh
- **OS:** Android 8.1 (Oreo), upgradable to Android 9.0 (Pie)

