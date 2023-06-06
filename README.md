# twrp_device_xiaomi_aquila
TWRP device tree for Xiaomi CC9 Unreleased Version(aquila)

The Xiaomi CC9 Unreleased Version (codenamed _"aquila"_) is factory version smartphones from Xiaomi.

## Features

**Works**

- Booting.
- ADB
- MTP
- Vibration

**Bug**

- Decryption

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/aquila" name="SakuraNotStupid/twrp_device_xiaomi_aquila" remote="github" revision="android9" />
```

Use ccache
```
#Enable ccache
export USE_CCACHE=1
export CCACHE_EXEC=$(which ccache)
```

Finally execute these:

```
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch omni_aquila-eng
mka recoveryimage
```

To test it:

```
fastboot flash recovery out/target/product/aquila/recovery.img
```
