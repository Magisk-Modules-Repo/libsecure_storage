# **libsecure_storage companion for rooted Samsung devices**

## Description

This Magisk module allows rooted Samsung Galaxy S10e/S10/S10+/S10+ 5G
(G970F/G973F/G975F/G977B), Note 10/10+/10+ 5G (N970F/G975F/G976B), S9/S9+
(G960F/G965F), Tab S4 (T830/T835), Tab S5e (T720/T725), Tab S6 (T860/T865),
Galaxy Fold/Fold 5G (F900F/F907B) and other devices to function without losing
Bluetooth pairings after a reboot.

## Android 10 and later

When Android 10 is detected, the `libbluetooth.so` library on your device will
be masked. Rather than include a patched version of the library in the module,
an attempt will be made to prepare a patched copy from the library on your
device.

If patching fails at installation time, your device is either unsupported or
has already had its `libbluetooth.so` hard-patched (e.g. by the
[Multi-disabler](https://forum.xda-developers.com/galaxy-s10/samsung-galaxy-s10--s10--s10-5g-cross-device-development-exynos/g97xf-multi-disabler-encryption-t3919714)).
If you find your device is unsupported, you are advised to migrate to Arthur
Trouillot's [Bluetooth Library
Patcher](https://github.com/Magisk-Modules-Repo/BluetoothLibraryPatcher)
module. That module more comprehensively supports Android 10 devices and it is
not my intention to duplicate that effort here. Android 10 support in the
**libsecure_storage companion** should be regarded as transitional.

## Android 9 and earlier

The module contains modified `libsecure_storage.so` libraries for use on these
systems. These modified versions will be used to mask the ones on your device.

After installing the module, you may wish to manually edit
`/system/etc/init/secure_storage_daemon.rc` or
`/vendor/etc/init/secure_storage_daemon.rc` (if either exists) to change the
line that reads:

```
start secure_storage
```

to:

```
stop secure_storage
```

Whilst not required, this extra step will prevent the secure storage daemon
from running unnecessarily. This change cannot be dynamically applied by
Magisk, because the file is read early in the boot process before Magisk runs.

No files other than the ones provided by this module are required.

## Testing

The module was developed and has been tested on Android 8.x (Oreo), 9.x (Pie)
and 10.

## Changelog

2020-05-09: v2.1

- Support Snapdragon devices updated to Android 10.

- Improve robustness of detecting successful patch of libbluetooth.so.
    
- Fix mode of patched libbluetooth.so to match original.

2019-12-13: v2.0

- Android 10 support added. When Android 10 is detected at installation time,
  the module will create a modified version of `libbluetooth.so` from the
  native library and mask this instead of `libsecure_storage.so`.

  Tested and verified on S10 series BSKO firmware and N10 series BSL7
  firmware.

  Thank you to Arthur Trouillot for finding the byte sequence to be patched.

2019-09-06: v1.8

- Remove files that were used to treat delayed Bluetooth initialisation. It's
  not clear which devices, if any, need these, and certainly no Samsung device
  launched in 2019 needs them.

- Android 9 (Pie) support is now deemed stable and will no longer issue a
  warning.

2019-03-29: v1.7

- Updated for Magisk v19 template format.

2019-03-21: v1.6

- S10e/S10/S10+ doesn't suffer from delayed Bluetooth initialisation, so it is
  exempt from installation of the extra support files for Pie devices added in
  v1.5.

2019-02-27: v1.5

- Install extra files on Pie devices to restore undelayed Bluetooth
  initialisation.

2019-02-27: v1.4

- Experimental Pie support: Explicitly check for the actual location of files
  to be masked and act as required.

2019-02-25: v1.3

- Add installation check for Android 8.x and issue warning if different.

2019-02-20: v1.2

- Update to latest Magisk template.

- Minimum version of Magisk now v17.0.

- Documentation updates.

2018-09-06: v1.1

- Changed docs to include Tab S4 (T830/T835) and no longer be S9-specific.

2018-06-24: v1.0

- Initial release.
