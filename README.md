# **libsecure_storage companion for rooted Samsung (Oreo) devices**

## Description

This Magisk module contains modified `libsecure_storage.so` libraries that allow rooted Samsung Galaxy S9/S9+ (G960F/G965F), Tab S4 (T830/T835) and probably other devices running Android 8.x (Oreo) to function without losing Bluetooth pairings after reboot.

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

The use of this module on non-Oreo systems is untested. Installing it on such devices may actually create issues whilst solving none.

## Changelog

2019-02-20: v1.2

- Update to latest Magisk template.
- Minimum version of Magisk now v17.0.
- Documentation updates.

2018-09-06: v1.1

- Changed docs to include Tab S4 (T830/T835) and no longer be S9-specific.

2018-06-24: v1.0

- Initial release.
