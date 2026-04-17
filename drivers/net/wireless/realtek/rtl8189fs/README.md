# rtl8189fs-20230207
RTL8189FS/FTV Linux Driver modified for FPV, v5.15.6-11-20230207  
The chip uses very little PCB area (QFN 4x4), and it's really cheap (\~$0.8 for a new module/\~$0.2 for a second-hand),  
so it's good to integrate if the SoC has a spare SDIO, for some flights less than 500m, or wireless configuring the SoC.  

Tested: 
 - Kernel 6.17 compat
 - TX power 
 - Monitor & injection, 802.11b(CCK)/g/n rates

Need test or can be further investigated:
 - 5M/10M bandwidth, only tested on a spectrum analyzer, and the spectrum seems good
 - 40MHz bandwidth
 - Channel scanning, MTU, ...

Not working:
 - STBC/LDPC not supported by hardware

### Use with OpenIPC
See [Platform Compatibilities](https://github.com/libc0607/rtl8822cs-20240221?tab=readme-ov-file#platform-compatibilities)  
The output of `find /sys/bus/sdio/devices/* | xargs -I {} cat {}/uevent | grep "SDIO_ID=" | cut -d= -f2` is `024C:F179`.  

### Resources 
It's very similar to RTL8188FU/RTL8188FTV, only with a different interface to the host  

Original driver: [rtl8189FS_linux_v5.15.6-11-g51d21ab4e.20230207.tar.gz](https://github.com/user-attachments/files/23749117/rtl8189FS_linux_v5.15.6-11-g51d21ab4e.20230207.tar.gz)  
Release Note: [ReleaseNotes.pdf](https://github.com/user-attachments/files/23749135/ReleaseNotes.pdf)  
Chip datasheet: [RTL8189FTV-VC-CG_Datasheet.PDF](https://github.com/user-attachments/files/23749248/RTL8189FTV-VC-CG_Datasheet.PDF)  
Chip schematic: [芯片引脚+封装原理图](https://github.com/user-attachments/assets/a6062269-71bc-4572-a51e-6740e4d5f721)  
Module datasheet: [BL-M8189FS6(VC)_Module_Specification_V1.0.2.1.pdf](https://github.com/user-attachments/files/23749225/BL-M8189FS6.VC._Module_Specification_V1.0.2.1.pdf)  

![芯片引脚+封装原理图](https://github.com/user-attachments/assets/448862f0-e384-42dd-8e62-92009cda37d1)  
<img width="854" height="611" alt="wifi模块" src="https://github.com/user-attachments/assets/8b348f81-1cf4-41b4-aa9e-b5c8bfc6a5ca" />  

\*Source: [RTL8189FTV开发资料](https://download.csdn.net/download/weixin_41586634/13986992)


### Why I'm doing this
Someone: “RTL8731BU (~$2.5) is too expensive (for FPV). Any choice at $0.3 ~ $0.4?”  

<img width="1080" height="534" alt="image" src="https://github.com/user-attachments/assets/ee3c0ded-2902-4e30-a9eb-c5bfc89810c4" />

