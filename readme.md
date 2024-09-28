# Samsung SM-J415FN (Galaxy J4+)

## Notes
btw, im an Arch user.

### Get odin and adb

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

## Development Notes

### Useful Links
- [Official Samsung Support](https://www.samsung.com/support/)
- [XDA Developers Forum](https://forum.xda-developers.com/)
- [Lineageos 19.1 for Samsung](https://xdaforums.com/t/unofficial-12-1-lineageos-19-1-for-galaxy-j4-j4primelte.4517067)
- [TWRP](https://twrp.me/samsung/samsunggalaxyj4plus.html)
- [Odin for Arch Linux](https://aur.archlinux.org/packages/odin4-cli)

### To-Do
- [ ] Research custom ROM
- [ ] Test root methods
- [ ] Document any issues and fixes




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

## Development Notes

### Useful Links
- [Official Samsung Support](https://www.samsung.com/support/)
- [XDA Developers Forum](https://forum.xda-developers.com/)
- [Lineageos 19.1 for Samsung](https://xdaforums.com/t/unofficial-12-1-lineageos-19-1-for-galaxy-j4-j4primelte.4517067)
- [TWRP](https://twrp.me/samsung/samsunggalaxyj4plus.html)
- [Odin for Arch Linux](https://aur.archlinux.org/packages/odin4-cli)

### To-Do
- [ ] Research custom ROM
- [ ] Test root methods
- [ ] Document any issues and fixes

