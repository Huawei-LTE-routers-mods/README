Huawei LTE modems and routers modifications
===========================================

This group of git repositories (or "organization", as Github calls it) contains Huawei LTE portable routers' modified (custom) firmware and web interface source code, with software packages and scripts included in the firmware.

These custom firmwares contain features not found in original official device firmware. Here are some of them:

* Support for IPv6 in mobile networks
* Root ADB & Telnet access
* Full-featured versions of busybox and iptables
* Full access to AT commands
* Change IMEI
* IPv4 Time to Live and IPv6 Hop Limit mangling
* Autonomous censorship circumvention for Deep Packet Inspection systems (with [zapret](https://github.com/Huawei-LTE-routers-mods/zapret))
* DNS over TLS support (with stubby)
* DNS-level advertisement blocker (with dnsmasq + [shakal](https://4pda.ru/forum/index.php?s=&showtopic=275091&view=findpost&p=89665467) lists)
* [Extended menu on OLED screen](https://github.com/Huawei-LTE-routers-mods/huawei_oled_hijack)
* TUN/TAP support (for OpenVPN and other VPN programs)
* OpenVPN, curl and other software
* Entware application repository support
* EXT4 kernel module and swap support
* Multilingual web interface with GSM/UMTS/LTE band selection menu

Many features are created by [@ValdikSS](https://github.com/ValdikSS/), while others are done by [@rust3028](https://github.com/rust3028/), [@ilya-fedin](https://github.com/ilya-fedin/), and others.


The packages are built with:

* [Android NDK r16b](https://developer.android.com/ndk/downloads/older_releases.html#ndk-16b-downloads), for bionic libc builds
* [Linaro GCC 4.9.4-2017.01 arm-linux-gnueabi](https://releases.linaro.org/components/toolchain/binaries/4.9-2017.01/arm-linux-gnueabi/), for glibc builds

The following CFLAGS are used:

```
# Balong Hi6921 V7R11 (E3372h, E5770, E5577, E5573, E8372, E8378, etc) and Hi6930 V7R2 (E3372s, E5373, E5377, E5786, etc)
# softfp, vfpv3-d16 FPU

CFLAGS="-march=armv7-a -mfloat-abi=softfp -mfpu=vfpv3-d16 -mthumb -O2 -s"


# Balong Hi6920 V7R1 (E3272, E3276, E5372, etc)
# soft, novfp

CFLAGS="-march=armv7-a -mfloat-abi=soft -mthumb -O2 -s"
```

Some notes:

* Most repositories contain `build.sh` script which is used to build the package/firmware for Huawei devices.
* Most software is linked against static libraries if they are small or not used anywhere except this software. For example, `openssl` is built as a dynamic library, `curl` utility links with static `libcurl` and `zlib` and dynamic `openssl`, `stubby` links with dynamic `openssl` and static `getdns` and `libyaml`, etc. To make static linking easier, statially linked libraries are built as static-only (.a files).
