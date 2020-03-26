If you have Huawei E5770, E3372h, E5573, E5577 with newer firmware versions which you don't know Flash Code/Datalock for, you can trick flashing software on the modem to skip Flash/Datalock code requirement by changing firmware version of the file you want to flash to the current firmware version installed on the device.

Flashing software on the router would think that you're trying to install the same firmware version, and will skip some sanity and security checks.

To do this, you'll need:

*   [qhuaweiflash](https://github.com/forth32/qhuaweiflash) by Forth32
*   [make_pkg_secure_1.3 with leaked Huawei keys](https://4pda.ru/forum/index.php?s=&showtopic=744265&view=findpost&p=62139559) (includes the key with hash `778a8d175e602b7b779d9e05c330b5279b0661bf2eed99a20445b366d63dd697`)

Open your firmware file in qhuaweiflash, change firmware version of the first firmware partition (usually it is _ptable_, but could be _fastboot_ in some cases).

The next step is to re-sign the firmware.  
First, remove the original signature by executing "sign" program with "-r" flag.  
Second, if your firmware file does not include web interface, sign it like this:

`sign -s E5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_r E5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_s private.key public.key -sv 1.3`

Where 5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_r — firmware without the signature (after sign -r), and  E5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_s — output file, ready to be flashed to the device.

If your firmware has a firmware and a web interface, sign it like this:

`sign -s E5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_r E5770s_DOWNGRADE_o2_21.318.01.01.1217_to_21.180.99.10.00_signed.fw_s private.key public.key -sv 1.3 -i ISO:WEBUI_17.100.20.03.306_MRE5 WEBUI:WEBUI_17.100.20.03.306_MRE5`

Where `WEBUI_17.100.20.03.306_MRE5` is the webui version (you can check it in the web interface of your router).
