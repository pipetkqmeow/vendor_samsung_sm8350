# vendor_samsung_sm8350 — o1q (Samsung Galaxy S21 5G, SM-G9910)

Proprietary vendor tree for the LineageOS 23.2 build of the SM-G9910
(Snapdragon 888). Generated with `extract-files.py` from a root dump of
the stock vendor partition:

* Firmware: **G9910ZHSGHZB1** (One UI 7, Android 15)
* 966 blobs, validated file-by-file against the device
* Blob fixups applied automatically (libsec-ril DDS patch, keymaster
  libcrypto, dpps libtinyxml2, wvhidl crypto shim, unihal ui shim)

## Usage in a build tree

Clone as `vendor/samsung/o1q`:

```bash
git clone <this-repo> vendor/samsung/o1q
```

(the device tree `device/samsung/o1q` inherits
`vendor/samsung/o1q/o1q-vendor.mk` automatically).

## Regenerating after a firmware update

A ready-to-use extraction environment is kept in `loswork/losroot`
(tools + prebuilts). To re-extract from a new dump:

```bash
adb shell su -c "tar cf - -C / vendor | gzip -1 > /data/local/tmp/vendor_dump.tar.gz"
# pull it, unpack to loswork/losroot/dump/ then:
cd loswork/losroot/device/samsung/o1q
./extract-files.py ../../../dump
cp -a ../vendor/samsung/o1q/. <this-repo>/
```

## IMPORTANT

This is a **private** vendor tree: do not publish the blobs (they are
Samsung/Qualcomm proprietary code, redistribution outside of the
LineageOS infrastructure is not permitted).
