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
* Autonomous censorship circumvention for Deep Packet Inspection systems
* DNS over TLS support
* DNS-level advertisement blocker
* Extended menu on OLED screen
* TUN/TAP support (for OpenVPN and other VPN programs)
* OpenVPN, curl and other software
* Entware application repository support
* EXT4 kernel module and swap support
* Multilingual web interface with GSM/UMTS/LTE band selection menu

Many features are created by [@ValdikSS](https://github.com/ValdikSS/), while others are done by [rust3028](rust3028), [ilya-fedin](https://github.com/ilya-fedin/), and others.


The packages are built with:

* [Android NDK r16b](https://developer.android.com/ndk/downloads/older_releases.html#ndk-16b-downloads), for bionic libc builds
* [Linaro GCC 4.9.4-2017.01 arm-linux-gnueabi](https://releases.linaro.org/components/toolchain/binaries/4.9-2017.01/arm-linux-gnueabi/), for glibc builds


Some notes:

* Most repositories contain `build.sh` script which is used to build the package/firmware for Huawei devices.
* Most software is linked against static libraries if they are small or not used anywhere except this software. For example, `openssl` is built as a dynamic library, `curl` utility links with static `libcurl` and `zlib` and dynamic `openssl`, `stubby` links with dynamic `openssl` and static `getdns` and `libyaml`, etc. To make static linking easier, statially linked libraries are built as static-only (.a files).
