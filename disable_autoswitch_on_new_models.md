E3372-320, E8372-320 and other newer modems with firmware version 10.x.x.x try to automatically detect PC operating system (Linux/macOS or Windows) and switch the mode accordingly. This is done by detecting USB Get Max LUN request from the operating system to device's CD-ROM.

Automatic switching creates race condition, complicating operating system-driven switching to other modes (NCM, for example).

To prevent this behaviour on Linux (for example, on the router running OpenWRT), one should set SINGLE_LUN quirk for usb-storage module.

Like this:

```
# cat /etc/modprobe.d/huawei-noprobe.conf

options usb-storage quirks=12d1:1f01:s
```
