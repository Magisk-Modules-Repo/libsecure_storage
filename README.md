# **libsecure_storage companion for rooted Samsung devices**

## Description

This Magisk module contains modified `libsecure_storage.so` libraries that allow rooted Samsung Galaxy S9/S9+ (G960F/G965F), Tab S4 (T830/T835) and probably other devices to function without losing Bluetooth pairings after a reboot.

This module was developed and tested using Android 8.x (Oreo). It is known to work well on systems running both 8.0 and 8.1.

Since v1.4, the module provides experimental support for Android 9.x (Pie) systems).

After installing this module, you may wish to manually edit `/system/etc/init/secure_storage_daemon.rc` to change the line that reads:

```
start secure_storage
```

to:

```
stop secure_storage
```

Whilst not required, this extra step will prevent the secure storage daemon from running unnecessarily. This change cannot be dynamically applied by Magisk, because the file is read early in the boot process before Magisk runs.

No files other than the ones provided by this module are required.

## Changelog

2019-02-27: v1.4

- Experimental Pie support: Check the actual location of files to be masked.

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
