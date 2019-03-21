# **libsecure_storage companion for rooted Samsung devices**

## Description

This Magisk module contains modified `libsecure_storage.so` libraries that allow rooted Samsung Galaxy S10e/S10/S10+ (G970F/G973F/G975F), S9/S9+ (G960F/G965F), Tab S4 (T830/T835) and probably other devices to function without losing Bluetooth pairings after a reboot.

The module was developed and tested on Android 8.x (Oreo) and 9.x (Pie). It is known to function as intended on the aforementioned device models.

Since v1.4, the module provides experimental support for Android 9.x (Pie) systems).

An extra issue affecting some Samsung Pie systems is that of delayed Bluetooth initialisation. As of v1.5, the module will install a number of extra files on Pie systems to remedy this problem. Version v1.6 adds an exemption for the S10e/S10/S10+ devices, as it has been ascertained that these systems do not suffer from delayed Bluetooth initialisation.

After installing this module, you may wish to manually edit `/system/etc/init/secure_storage_daemon.rc` (if it exists) to change the line that reads:

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

2019-03-21: v1.6

- S10e/S10/S10+ doesn't suffer from delayed Bluetooth initialisation, so it is exempt from installation of the extra support files for Pie devices added in v1.5.

2019-02-27: v1.5

- Install extra files on Pie devices to restore undelayed Bluetooth initialisation.

2019-02-27: v1.4

- Experimental Pie support: Explicitly check for the actual location of files to be masked and act as required.

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
