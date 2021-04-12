Balong modems support different USB modes: from plain old PPP modem up to Ethernet emulation and CDC NCM modem specification.  
The modes weren't documented before, so this is what's available on E3372-153.

Check drivers/usb/mbb_usb_unitary/{hw_pnp.c,hw_pnp.h,f_mass_storage.c,hw_pnp_adapt.c} for more information.
```
#define SC_REWIND_11 = 0x11

struct rewind_cmd_param
{
    USB_UINT8 bCmdReserved;         # 6
    USB_UINT8 bPcType;              # WINDOWS_OS_FLAG=0x00, MAC_OS_FLAG=0x10, LINUX_OS_FLAG=0x20, GATEWAY_OS_FLAG=0x30
    USB_UINT8 bTimeOut;
    USB_UINT8 bPID;
    USB_UINT8 bNewPID;
    USB_UINT8 bSupportCD;
    USB_UINT8 bProFile;             # GATEWAT_MODEM_MODE=0, GATEWAY_NDIS_MODE=1
    USB_UINT8 bGreenMode;           # USB_RNDIS=1
    USB_UINT8 reserved[USB_NUM_7];
};


Strings for usb_modeswitch

Old PPP mode:
55534243123456780000000000000011063000000100000000000000000000

RNDIS mode:
55534243123456780000000000000011060000000100000100000000000000

CDC Ethernet mode:
55534243123456780000000000000011062000000101000100000000000000

CDC NCM (modem) mode:
55534243123456780000000000000011063000000000010000000000000000


555342431234567800000000000000     11             06         20       00       00   01        01        00        01    00000000000000
                               SC_REWIND_11  bCmdReserved  bPcType  bTimeOut  bPID bNewPID bSupportCD bProFile bGreenMode  reserved
```

Besides SC_REWIND_11 older models may have SC_MAC_SYS (0xbb), SC_WIN_SYS (0xa2) SCSI commands.  
Additional switching functionality is also present for USB gadget (not CD-ROM). Check  
https://github.com/hisili/E5573Cs/blob/bbc208728a449bbe72cca158283d682305fe3bca/drivers/usb/mbb_usb_unitary/hw_pnp.c#L3033
