# **libsecure_storage companion for rooted Samsung (Oreo) devices**

## Description

This Magisk module contains modified `libsecure_storage.so` libraries that allow Samsung Galaxy S9/S9+ (G960F/G965F), Tab S4 (T830/T835), and probably other rooted devices running Android 8.x to function without losing Bluetooth pairings after reboot.

After installing this module, you may wish to manually edit `/system/etc/init/secure_storage_daemon.rc` and change the line that reads **start secure_storage** to **stop secure_storage**. This step is not required, but will prevent the secure storage daemon from running unnecessarily. This change cannot be applied by Magisk, because the file is read and acted upon early in the boot process before Magisk runs.

Use of this module on non-Oreo systems is untested. The problem it addresses may not exist on other versions of Android, and installing it on such devices may actually create problems.

## Changelog

2018-09-06: v1.1

- Changed docs to include Tab S4 (T830/T835) and no longer be S9-specific.

2018-06-24: v1.0

- Initial release.
