# Huawei Balong Open Source Software

Source code for Huawei Balong LTE routers and modems is available in two website sections:

[https://consumer.huawei.com/en/opensource/](https://consumer.huawei.com/en/opensource/)  
[https://consumer.huawei.com/en/search/?keyword=source](https://consumer.huawei.com/en/search/?keyword=source) (press "support" button)  
[https://consumer.huawei.com/en/search/?keyword=gpl](https://consumer.huawei.com/en/search/?keyword=gpl) (press "support" button)

The mirror is available on my FTP: [ftp://serv.valdikss.org.ru/Downloads/Huawei_Open_Source/](ftp://serv.valdikss.org.ru/Downloads/Huawei_Open_Source/)

To my knowledge, all source code archives are semi-broken/incomplete. Archives have incorrect
configuration, defines in structs (which break their offsets/sizes), etc.  
As far as I'm aware, nobody yet has build working kernel for any device from provided source code.

Yet the source code is useful for binary analysis of the firmware.  
Almost all the code could be reused within the chip family.

```
Hi6950
Balong V7R5:  B612s-25d_open_src.rar
              B618s-22d.opensource.rar

Hi6932
Balong V7R22: E5885Ls-93a_open_src.rar
              hi6932_ME919Bs-821bN_2018-03-01-kernel-opensource.tar.gz
              B528s-23a.opensource.tar.gz

Hi6921
Balong V7R11: opensrc.tar.gz ("E3372h-153-open resource code") (E3372 h model)
              B310&B315 open source code part{1,2}.rar
              E5770s-923_open_src.rar
              E8372h-153_open_source.rar
              E5573Cs-609_open_src.rar (probably, not sure, it's either R11 or R2)

Hi6930
Balong V7R2:
              E3372s-153 Open Source.part{1,2,3}.rar (E3372 s model)

Hi6920
Balong V7R1:  E5372_GPL_Code.tar.gz
```
