# Device Tree for OnePlus 7T Pro(hotdog)

The OnePlus 7T Pro (codenamed _"hotdog"_) is a flagship smartphone from OnePlus.
It was released in September 2019.




## Compile

First download the platform_manifest_twrp_omni tree:

```
repo init --depth=1 -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
```

Then create `.repo/local_manifests/roomservice.xml` and add the following: 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="kimocoder/android_device_oneplus_hotdog_unified_TWRP" path="device/oneplus/hotdog" remote="github" revision="master" />
</manifest>
```

Now sync your source:

```
repo sync
```

Next download and extract https://gerrit.omnirom.org/changes/android_build~33182/revisions/5/files/core%2FMakefile/download. Rename extracted file to `Makefile` and copy to `build/make/core`.

Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch omni_hotdog-eng 
mka adbd recoveryimage 
```

To test it:

```
fastboot boot out/target/product/hotdog/recovery.img
```

Kernel Source: precompiled stock one
## Credits
