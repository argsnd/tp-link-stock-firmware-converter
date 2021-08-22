# tp-link-stock-firmware-converter
The live branch contains a pre-compiled version of this tool. If you wish to compile your own, you may follow these instructions.

1. Install Emscripten.
2. Download [tplink-safeloader.c](https://github.com/openwrt/openwrt/blob/master/tools/firmware-utils/src/tplink-safeloader.c), [md5.c](https://github.com/openwrt/openwrt/blob/master/tools/firmware-utils/src/md5.c), and [md5.h](https://github.com/openwrt/openwrt/blob/master/tools/firmware-utils/src/md5.h) from the OpenWrt repository to this directory.
3. Compile tplink-safeloader with emscripten: 
```bash
emcc tplink-safeloader.c md5.c -o safeloader.js -s FORCE_FILESYSTEM=1 -s EXIT_RUNTIME=1 -s EXTRA_EXPORTED_RUNTIME_METHODS=FS
```
4. Run safeloader.html from a web server such as `python3 -m http.server` as most browsers don't support file:// XHR requests.
