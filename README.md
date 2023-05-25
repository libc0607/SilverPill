# SilverPill
这里以后会放一些关于 AGM MCU 的内容  
[板](https://oshwhub.com/libc0607/agrv2k_silverpill_v1p2)都画了，总不能一直吃灰，但还没想好写哪些，先新建咕着  

## 一些准备
### 开发板
你可以看看我的 AGRV2K48/AG32VF103 板子：[OSHWHub: libc0607/agrv2k_silverpill_v1p2](https://oshwhub.com/libc0607/agrv2k_silverpill_v1p2)  
另外由于它和 STM32F 系列兼容，所以你随便找个 STM32F103 板子焊个 AGM 上去也行  

### 下载器 
这个芯片支持 SWD（2线） 和 JTAG（4线？）调试，可以读写到这个 Flash，所以可以用来下载  
另外，还可以通过设置 BOOT0 和 BOOT1 使 CPU 启动到 BootROM，然后就支持串口下载了，程序和 Bitstream 都通过这个下载  

这个系列的芯片是一起封了个 SPI Flash，在默认配置下这个 Flash 会被分成两部分，Flash 末尾的 100kBytes 用于存储 FPGA 部分的 Bitstream（实际大小为 99,944 Bytes），前面剩下的部分则是 CPU 执行的代码  
你可能需要明白的是：上电后 CPU 从 BootROM（0x10000）开始执行，读取 BOOT0 和 BOOT1 的状态；如果是设置为从 Flash 启动，CPU 会先主动从 Flash 读取 Bitstream 并通过 FCB 控制器加载其到 FPGA 中；再跳转到 0x80000000 执行用户代码  

总之根据你自己的需求准备即可，我自己的话只是用了个 WCH-Link

### 官方资料 
你应当能够在 http://www.tcx-micro.com/ 找到全部的资料，以这里为准  

### 第三方资料
寂寞鸽在 whycan 的贴子：[【新玩具get】AGM AGRV2K，16.8块钱的MCU+FPGA二合一芯片 @metro](https://whycan.com/t_9523.html)  
PlatformIO 开发包：[Telegram](https://t.me/agmfpgadoc/106)  
AGM32 peripharals 特性文档：[Telegram](https://t.me/agmfpgadoc/80)  
MCU 兼容 peripharals 参考文档：[Telegram](https://t.me/agmfpgadoc/95)  

另外，认真阅读这些内容有助于更好地理解 AGM 的芯片，但你应该假装没有看到  
[Github: pablomarx/rodinia](https://github.com/pablomarx/rodinia)  
[Github: gabonator/AltaGateReverse](https://github.com/gabonator/Education/tree/master/2021/AltaGateReverse)  
[AGRV2K/AG32(p1030g0?) BootROM @0x10000+8kB](https://t.me/agmfpgadoc/109)，[Ghidra](https://ghidra-sre.org/)  

### 开发环境
[AGM MCU AG32 IDE 开发环境搭建（23年5月新版）](http://www.tcx-micro.com/doc_26307400.html)  
[AGM MCU AG32 在 VSCode 下的使用入门（23年5月新版）](http://www.tcx-micro.com/doc_26309003.html)   

## 关于这个芯片的一些细节  
待填坑  
……对，我本来是主要想写这个，上面都是凑字数的


