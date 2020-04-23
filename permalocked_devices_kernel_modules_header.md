### Note for permanently-locked devices' kernel modules

Huawei, to prevent existing (sim-unlocking) kernel modules from being loaded, has changed kernel module header layout on permanently-locked devices with 329+ operator firmware.
Now the kernel header is one DWORD (4 bytes) larger. The latest DWORD gets dereferenced, which causes kernel panic of the device on `insmod`.

The easiest way to fix that is as follows:

```
--- include/linux/module.h      2020-04-23 21:20:38.354018956 +0300
+++ include/linux/module.h      2020-04-23 21:20:46.116095477 +0300
@@ -225,7 +225,8 @@
        struct list_head list;
 
        /* Unique handle for this module */
-       char name[MODULE_NAME_LEN];
+       char name[MODULE_NAME_LEN + 4]; // for 333 firmware, with signature
+//     char name[MODULE_NAME_LEN]; // for 328 firmware, without signature
 
        /* Sysfs stuff. */
        struct module_kobject mkobj;

```

Global non-locked 329+ firmware have only X.509 digital signature, which is already patched by `patchblocked.sh` (in `huawei_balong_modfw_kitchen`), without header modification.
