>  Hackintosh-Ryzen-3500X-MSI-B450M-Mortar-MAX

## 主要配置

- AMD Ryzen 3500X

- MSI B450M Mortar Max

- RX580 4G 2304sp

- 板载有线网卡以及 AX200

## 引导版本

- OpenCore 0.6.0

## 系统版本

- Catalina 10.15.6

## BIOS 设置

### 关闭

- CSM
- Memory Fast Boot
- Serial(COM) Port（请务必关闭，不关闭会影响睡眠）

### 开启

- XHCI Hand-off （默认开启）
- USB设备从S3/S4唤醒（如需要鼠标键盘唤醒则开启）
- Above 4G memory（会影响 Win10 下的板载有线网卡）

我是双系统用户，在这块主板上开启 Above 4G memory 会导致 Win10 下板载有线网卡无法使用，如果你是**单 Mac 系统**用户可以开启，然后在 boot-args 中移除 ncpi=0x2000 即可。**双系统用户建议不要开启**，不会影响黑苹果系统。这个东西虽然很多地方都推荐开启，但是我目前没发现有什么必要。

## 使用

### USB 端口定制

同主板的我已经定制了 USB 口，理论上不需要修改了，内建了蓝牙和鼠标键盘的机箱后部 2.0 口，为保证端口数量不超出15个限制，限制了后部 USB 3.0 口的 2.0兼容（即只支持3.0），前面板的端口一切正常。

希望重新定制的请删除 **/kexts/USBPorts.kext**，自行重新定制即可。

### 三码

~~**配置中我已经移除了三码，请自行添加**。~~

鉴于部分网友不看此说明导致出现如下安装问题：

**请注意：安装时提示 此版本不支持该平台 系未注入机型及三码导致**

我添加了一个预设的机型 iMacPro1,1 与三码，如需使用 AppleID 请自行更换三码，否则请自行承担后果。

### 网卡

我常规使用有线网卡，AX200 的蓝牙使用没有问题，WIFI驱动和蓝牙驱动请关注[远景大神qcwap2012](http://bbs.pcbeta.com/viewthread-1848662-1-2.html)制作的驱动，这是他的[仓库地址](https://github.com/OpenIntelWireless/itlwm)。有需要的**请自行添加。**

### 其他

- 声卡和网卡我在 **DeviceProperties** 下进行了注入，如果无法正常使用请自行修改。
- ACPI 下的 SSDT-EC.aml 我是针对这款主板进行定制的，其他主板请自行解决。
- 其他如 CPU变频，电源睡眠唤醒，显卡加速等均正常使用。
- 此前由于我将 catalina 安装在单独的 SATA 固态上，单盘引导单系统，故对应修改了 scanPolicy 值，导致使用配置的人无法扫描到安装选项，**现已修改至 0，扫描全部类型磁盘.**
- 远景帖子[链接](http://bbs.pcbeta.com/viewthread-1866498-1-1.html)

## 鸣谢

https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/

https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html

https://dortania.github.io/Getting-Started-With-ACPI/

https://blog.xjn819.com/?p=543

https://blog.daliansky.net/OpenCore-BootLoader.html