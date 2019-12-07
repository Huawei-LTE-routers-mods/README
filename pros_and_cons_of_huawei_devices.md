Huawei produces high quality hardware with their own sensitive radio and Wi-Fi modules, but they don't care about end users, you will get absolutely no support from Huawei. For example, E5885 router has broken USB networking in Linux; contacting support 5 times during the year did not help the problem, you'll be asked for your device IMEI and serial number once and won't receive further replies for update requests. In case of any problems, you're on your own.

Pros for general consumers:

*   Huawei LTE devices are easy to use, fast and stable
*   High radio sensitivity
*   Over the air automatic/manual firmware updates

Cons for general consumers:

*   Huawei is not oriented for retail, most models are hard to buy or available only in China
*   No support from the manufacturer in case of any problems
*   No USSD commands support in stock web interface, unable to get balance and other information if operator use only USSD interface
*   Missing models and model specifications on Huawei website
*   Some models are pricey

Huawei does not publish firmware files for the devices, and even if you have one, you can't flash it right away anyway: firmware installation process require special flash code which you can obtain from Huawei (but see first paragraph), buy online from websites with access to Huawei mobile operator area, or for older devices, generate it using code generator which was made by reverse engineering kernel code. Firmware files are signed with cryptographic signature.

Huawei also could not care less about Open Souce. The company publish broken source code archives on their website which either do not compile or run on the device, only to mimic GPL compliance. No instructions to run your own compiled source code are provided, that's impossible to do without third-party utilities made by reverse engineering of the bootloader and other system components.
GPL is blatantly violated: some closed source Huawei utilities are based on widespread utilities, for example `libwl.so` library is based on `iw` utility source code, even `main()` function is still in there.

Pros for firmware hackers and power users:

*   IMEI can be changed to circumvent some operators tethering limitations
*   Linux, VxWorks and M3 consoles are accessible on most devices
*   Linux userspace mostly uses well-known utilities, techniques and protocols
*   Lots of debugging printf's in userspace and kernelspace
*   TUN/TAP, EXT4 and other modules could be compiled from Huawei kernel source code
*   Firmware could be modified and rebuilt

Cons for firmware hackers and power users:

*   Lots of security features designed to protect against unauthorized modification need to be circumvented
*   Broken kernel sources won't allow you to compile custom kernel and run it
*   Some models have Secure Boot enabled which block unauthorized kernels and usbloaders and other region firmwares