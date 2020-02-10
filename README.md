# 微星 B360M 迫击炮（钛金版）黑苹果 OpenCore EFI

## EFI 介绍
此 EFI 使用`iMac19,1`机型，微星 B360M 迫击炮（钛金版）的绝大部分用户可通过修改使用，核显 + 独显共同硬解，默认启用全部 USB 端口，[OpenCore](https://github.com/acidanthera/OpenCorePkg) 版本：0.5.5<br>
<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Screenshots/About.png)

### 可正常工作
- [x] 声卡（板载）/ 网卡（板载）
- [x] 显卡（核显 + 独显）/ 硬解 4K（HEVC + H.264）
- [x] WiFi（PCI-E 设备） / 蓝牙（PCI-E 设备）
- [x] 隔空投送 / 接力 / 随航
- [x] FaceTime / iMessage
- [x] Apple Music / Apple TV Plus
- [x] 睿频 / HWP 变频 / 原生电源管理
- [x] 睡眠 / 键盘、鼠标唤醒
- [x] 其他白果功能（99%）

### 我的配置

|         硬件       |                   型号                     | 
|-------------------:|:------------------------------------------|
|               主板 | 微星 B360M 迫击炮                               |
|             处理器 | 英特尔酷睿 i5-9600K                            |
|               显卡 | 公版 RX 570 4GB（由微星代工）                    |
|               硬盘 | 西部数据 SN750 500GB                          |
|               内存 | 光威悍将 8GB DDR4 2666Mhz x 2                 |
|        无线 + 蓝牙 | 奋威 BCM94360CD（双频 1750M + 蓝牙 4.0）PCI-E 无线网卡  |
|  机箱 + 电源 + 散热 | 乔思伯 U3 + 台达 NX450 + 利民 AS120 + ARCTIC F12 PWM |
|             显示器 | 飞利浦 276E8VJSB（27 英寸 4K 分辨率）                 |
|     摄像头 + 麦克风 | 双飞燕 PK-838G 带麦克风摄像头                       |
|               音箱 | 漫步者 R19U 2.0 迷你音箱                           |
|               键盘 | iQunix F96 珊瑚海（有线茶轴 RGB 版）                 |
|               鼠标 | 罗技 MX Anywhere 2（使用优联连接，以方便在 BIOS 中使用） |

### 兼容的配置

|         硬件       |                              型号                           | 
|-------------------:|:------------------------------------------------------------|
|               主板 | 微星 B360M 迫击炮（钛金版）                                    |
|             处理器 | 英特尔第 8 代、第 9 代酷睿处理器（推荐拥有核显的版本）                |
|               显卡 | RX 560 / RX 570 / RX 580 / RX 590 / RX VEGA⁵⁶ / RX VEGA⁶⁴ / Radeon VII / RX 5500 XT / RX 5600 XT / RX 5700 / RX 5700 XT |
|               硬盘 | 除了几个特例（如三星 PM981），基本都可以                            |
|               内存 | 除了非常差的，基本都可以                                        |
|        无线 + 蓝牙 | 黑苹果免驱版无线 + 蓝牙 PCI-E 网卡都可以                          |
|     摄像头 + 麦克风 | macOS 免驱版都可以                                             |
|  机箱 + 电源 + 风扇 | 根据个人喜好和 CPU、显卡的功率来决定                               |
|             显示器 | 根据个人喜好选择（推荐 4K 分辨率）                                |
|  键盘 + 鼠标 + 音箱 | 根据个人喜好选择                                                |
|           其它外设 | 根据个人喜好选配                                              |

*显卡优先选择蓝宝石，其次选择迪兰恒进、华硕和微星，尽量不选择盈通和讯景，一定避开 RX 580 2048SP 版本！*<br>
*如果选择购买新显卡，推荐 RX 5500 XT、RX 5600 XT、RX 5700 和 RX 5700 XT 这四个型号。*<br>
*个人非常不推荐使用玄冰 400 散热器（不含扣具升级款），我已经更换为利民 AS120，远离反人类设计保平安。*

## 更新记录
#### 2020.02.10
修复 OpenCore 0.5.5 正式版将 PlatformInfo > Generic > SupportCsm 改名为 AdviseWindows 忘记更改配置文件的问题。<br>
*请手动更改该项名称，并建议按照官方示例文件调整 AdviseWindows 顺序至 Generic 下第一位。*

#### 2020.02.05
设置 TakeoffDelay 参数为 200 (Misc > Boot，单位：毫秒) 以支持引导过程的原生快捷键。<br>
*实测参数设置到 150 时便可触发原生快捷键，但触发概率较小，200 是较为均衡的数值，可将其适当调高，如 300~500 之间。*<br>
*在 OC 0.5.5 版本之前，我一直无法触发原生快捷键 (可能和键盘有关？)，如果你之前能触发，或仍不能触发，请在 Issues 讨论。*

#### 2020.02.04
更新 OpenCore 至 0.5.5 正式版；更新 AppleALC / VitualSMC 等 Kexts 至官方最新版；添加 UEFI Shell 工具（默认未启用）。<br>
*OC 0.5.5 正式版的配置文件新增了若干条目，建议按照使用习惯重新配置。*

#### 2020.02.02
更新支持读写硬件 NVRAM，不再需要模拟 NVRAM，请删除 `/EFI/nvram.plist` 文件。

#### 2020.01.14
更新 OpenCore 至 0.5.4 正式版；更新 Lilu / AppleALC / CPUFriend / VitualSMC / WhateverGreen 等 Kexts 至官方最新版。<br>
*OC 0.5.4 正式版的配置文件新增了若干条目，建议按照使用习惯重新配置，并删除`/EFI/OC/Drivers/virtualsmc.efi`文件（已被合并至 OC 中）。*

#### 2020.01.05
使用 OpenCore 官方补丁间接修复「不开启小憩无法进入睡眠」的问题，移除 SSDT-SBUS.aml 文件。<br>
*不开启小憩的目的是睡眠后不被自动唤醒，开启 OC 的「禁用 RTC 唤醒计划」补丁后，打开小憩功能可以正常进入睡眠，且不会被自动唤醒，间接达到「不开启小憩进入睡眠」的状态，如不需要可以手动关闭该补丁（感谢 [ArchFeh](https://github.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/issues/5) 针对文案的提醒）。*<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_Kernel_Patch.png)

#### 2019.12.29
更新 WhateverGreen.kext 至 1.3.6 最新编译版；修复「不开启小憩无法进入睡眠」的问题（理论上不该存在问题）。

#### 2019.12.23
更新 WhateverGreen.kext 至 1.3.6，修改 shikigva 代码为 80（可支持 Netflix）。

#### 2019.12.20
上传忘记添加的 SSDT-SBUS.aml（用来修复「不开启小憩无法进入睡眠」，但我发现好像仍然无法进入，待测试）。

#### 2019.12.19
经过三天的测试后，上传第一版。

## 使用 EFI
准备 [ProperTree](https://github.com/corpnewt/ProperTree) ([下载](https://github.com/GeQ1an/Personal/raw/master/Hackintosh/ProperTree.zip)) 或 [PlistEdit Pro](https://www.fatcatsoftware.com/plisteditpro/) 用来编辑配置文件，请勿使用其他编辑器编辑（切记）。<br>
OpenCore 拥有高度的可定制化，建议先参考下面的说明使用配置好的基础版本，之后再通过 [xjn 博客](https://blog.xjn819.com/?p=543) 和 [黑果小兵博客](https://blog.daliansky.net/OpenCore-BootLoader.html) 学习更多内容进行修改。

### BIOS 设置
*请先确定正在使用的 BIOS 版本，[迫击炮](https://cn.msi.com/Motherboard/support/B360M-MORTAR) 7B23v16 以上，[迫击炮钛金版](https://cn.msi.com/Motherboard/support/B360M-MORTAR-TITANIUM) 7B23vA6 以上，否则请参考官方文档升级 BIOS 至最新版本。*<br>
<br>
STTINGS\高级\PCI子系统设置\Above 4G memory/Crypto Currency mining [允许]<br>
<br>
STTINGS\高级\内建显示配置\设置第一显卡 [PEG]<br>
STTINGS\高级\内建显示配置\集成显卡多显示器 [允许] （如果使用拥有核显的处理器）<br>
<br>
STTINGS\高级\ACPI设置\电源 LED 灯 [双色]（如果选择 [闪烁]，睡眠时电源灯将不断闪烁）<br>
<br>
STTINGS\高级\USB设置\XHCI Hand-off [允许]<br>
STTINGS\高级\USB设置\传统USB支持 [允许]<br>
<br>
STTINGS\高级\电源管理设置\ErP Ready [允许]<br>
<br>
STTINGS\高级\Windows操作系统的配置\Windows 10 WHQL支持 [允许]<br>
STTINGS\高级\Windows操作系统的配置\MSI 快速开机 [禁止]<br>
STTINGS\高级\Windows操作系统的配置\快速开机 [禁止]<br>
<br>
STTINGS\高级\唤醒事件设置\唤醒事件管理 [BIOS]<br>
STTINGS\高级\唤醒事件设置\USB设备从S3/S4/S5唤醒 [允许]<br>
<br>
STTINGS\启动\启动NumLock状态 [关]（macOS 默认可使用数字键盘）<br>
STTINGS\启动\启动模式选择 [UEFI]<br>
<br>
OC(Overclocking)\CPU 特征\Intel 虚拟化技术 [允许]（必须）<br>
OC(Overclocking)\CPU 特征\Intel VT-D 技术 [禁止]（必须）<br>
OC(Overclocking)\CPU 特征\CFG锁定 [禁止]（必须！）<br>

### 直接使用
仅适合使用 9600K 处理器的用户！<br>
下载整包后，如果之前在 Clover 时就使用`iMac19,1`机型，可直接使用之前的三码，或使用 [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) （其他工具亦可）选择`iMac19,1`机型生成新的三码 + ROM，用 ProperTree 打开`/EFI/OC/config.plist`文件，填入到 PlatformInfo > Generic 位置中（如下图）。<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_PlatformInfo.png)<br>
保存后，先通过 USB 测试引导，无问题后将 EFI 文件夹放置到启动磁盘 EFI 分区，重启电脑。

### 修改使用
适合使用其他拥有核显处理器的用户。<br>
1. 填入`iMac19,1`机型的三码 + ROM 信息到`/EFI/OC/config.plist`文件 PlatformInfo > Generic 处。
2. 将`/EFI/OC/config.plist`文件 Kernel > Add > 10 和 11 中 Enabled 的`Ture`手动修改为`False`（如下图）。<br>
*默认的是 9600K 专用的 HWP 变频文件，其他处理器不可启用！*<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_Kernel_CPU.png)
<br>
保存后，先通过 USB 测试引导，无问题后将 EFI 文件夹放置到启动磁盘 EFI 分区，重启电脑。

### 无核显使用
适合使用无核显处理器的用户。<br>
1. 填入`iMacPro1,1`机型的三码 + ROM 信息到`/EFI/OC/config.plist`文件 PlatformInfo > Generic 处，并将机型修改为`iMacPro1,1`。
2. 将`/EFI/OC/config.plist`文件 Kernel > Add > 10 和 11 中 Enabled 的`Ture`手动修改为`False`。<br>
*因 iMacPro1,1 机型不支持 HWP 变频，也可直接删除这两个条目和相关 kext 文件。*
3. 删除`/EFI/OC/config.plist`文件 DeviceProperties > Add > PciRoot(0x0)/Pci(0x2,0x0) 下 AAPL,ig-platform-id 这一行参数（如下图）。<br> 
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_DeviceProperties.png)
4. 右键点击`/EFI/OC/Kexts/USBPower.kext`文件——显示包内容，进入`Contents`文件夹，打开`Info.plist`文件，将机型修改为`iMacPro1,1`（如下图）。<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_USBPower_Info.png)
<br>
保存后，先通过 USB 测试引导，无问题后将 EFI 文件夹放置到启动磁盘 EFI 分区，重启电脑。

### 无独显使用
适合无独显、只使用核显的用户。<br>
1. 填入`Macmini8,1`机型的三码 + ROM 信息到`/EFI/OC/config.plist`文件 PlatformInfo > Generic 处，并将机型修改为`Macmini8,1`。<br>
2. 使用非 9600K 处理器，将`/EFI/OC/config.plist`文件 Kernel > Add > 10 和 11 中 Enabled 的`Ture`手动修改为`False`。<br>
*Macmini8,1 机型支持 HWP 变频，对于非 9600K 处理器可稍后自行定制 HWP 变频文件。*
3. 修改`/EFI/OC/config.plist`文件 DeviceProperties > Add > PciRoot(0x0)/Pci(0x2,0x0) 下 AAPL,ig-platform-id 参数为 07009b3e ，并新增 framebuffer-unifiedmem 参数为 00000080（如下图）。<br> 
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_DeviceProperties_I.png)
4. 右键点击`/EFI/OC/Kexts/USBPower.kext`文件——显示包内容，进入`Contents`文件夹，打开`Info.plist`文件，将机型修改为`Macmini8,1`。
<br>
保存后，先通过 USB 测试引导，无问题后将 EFI 文件夹放置到启动磁盘 EFI 分区，重启电脑。

### ~~模拟 NVRAM~~（不再需要）
~~无论是直接使用还是修改使用，都建议参考 [xjn 博客](https://blog.xjn819.com/?p=543) 的完善部分「3.1 模拟 NVRAM」，进行模拟 NVRAM 的操作。~~

### 进阶使用
1. 参考 [xjn 博客](https://blog.xjn819.com/?p=543) 的进阶部分「4.1 CPU 的变频优化」或 xjn 大佬发表于 PCBETA 的帖子 [FCPX 核显独显全程满速指南](http://bbs.pcbeta.com/viewthread-1836920-1-1.html) 中「HWP 变频」部分，根据个人需求定制`CPUFriendDataProvider.kext`HWP 变频文件，放入`/EFI/OC/Kexts/`替换同名文件，重新启用`/EFI/OC/config.plist`文件 Kernel > Add > 10 和 11。<br>
*iMac19,2 和 iMacPro1,1 均不支持 HWP 变频，无需尝试。对于有核显的用户建议选择 iMac19,1 机型，对于只使用核显的用户推荐 Macmini8,1 机型。*
2. 参考 [黑果小兵博客](https://blog.daliansky.net/Intel-FB-Patcher-USB-Custom-Video.html) 生成`USBPorts.kext`USB 定制文件，放入`/EFI/OC/Kexts/`替换同名文件，打开`/EFI/OC/config.plist`，关闭 Kernel > Add > 7，打开 8。<br>
*目录内有我的 USB 定制文件，可在备份好 EFI 的情况下尝试使用。*<br>
![](https://raw.githubusercontent.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/master/Images/Explain/ProperTree_Kernel_USB.png)

## Q&A
1. **开机时苹果 logo 显示不正常怎么办？**<br>
   有两个方法可以解决这个问题。<br>
   方法一：在`/EFI/OC/config.plist`配置文件 Misc—–Boot——Resolution 处填写正确的显示器分辨率；<br>
   方法二：将 BIOS「STTINGS\启动\全荧幕商标」设置为 [允许]。<br>
   两种方法选择其一即可，经反复测试，在微星 B360M 迫击炮（钛金版）上我更推荐方法二。<br>
   *如果同时使用方法一和方法二，开机 logo 的显示依旧会不正常。*
2. **无法正常进入睡眠状态怎么办？**<br>
   目前所知的情况是 ~~bugOS~~ 10.15.2 存在睡眠相关 bugs，如果使用了最新的 EFI 仍然无法正常进入睡眠，请尝试到「系统偏好设置——安全性与隐私——隐私——定位服务」关闭「Siri 与听写」。
3. **为什么推荐拥有核显的 CPU？**<br>
   首先，macOS Catalina 原生支持 4K 双硬解的独显最低为 RX VEGA⁵⁶，而第七代及以后的酷睿处理器核显可以和低于 RX VEGA⁵⁶ 的独显协同工作，完成 4K 双硬解；<br>
   其次，因为黑果没有 T2 芯片，所以没有核显的黑果无法使用随航（Sidecar）功能。
4. **引导过程触发原生快捷键怎么这么难？**<br>
   我也被这个问题困扰了许久，在 OC 0.5.5 之前尝试过各种配置组合，均无法触发，但 OC 更新 0.5.5 后，通过设置 TakeoffDelay 参数可在引导过程中触发原生快捷键，建议在启动时按住组合键，或键盘灯亮起时不断重按组合键，可自行调整 TakeoffDelay 参数。
5. **待更新**

## 结语
完成以上步骤后，基本上已经有了一个完成度为 99% 的黑苹果设备，更多截图请查看 [截图预览](https://github.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/tree/master/Images/Preview.md) 。<br>
黑果和白果不一样，各种补丁和新系统的兼容性可能存在问题，一旦稳定后，追新速度不要太快，待各路大佬测试、完善后再升级也不迟。

## 鸣谢
[xjn](https://blog.xjn819.com/)<br>
[andot](https://github.com/andot/MSI-B360M-MORTAR-IMACPRO-EFI/)<br>
[daliansky](https://github.com/daliansky) ([黑果小兵](https://blog.daliansky.net/))<br>
[tonymoses](http://bbs.pcbeta.com/viewthread-1835637-1-1.html)<br>
[cattyhouse](https://github.com/cattyhouse/oc-guide/)<br>
[osx86zh](https://t.me/osx86zh/) ([Telegram](https://telegram.org/) 讨论组)

## 友情链接
[OpenCorePkg 官方版本](https://github.com/acidanthera/OpenCorePkg/releases) [OpenCorePkg 自动编译](https://github.com/williambj1/OpenCore-Factory/releases)<br>
[AppleSupportPkg 官方版本](https://github.com/acidanthera/AppleSupportPkg/releases) [AppleSupportPkg 

## 写在最后
作为一个黑果小白，欢迎在 [Issues](https://github.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/issues) 或通过 [Telegram](https://t.me/GeQ1an) 联系我，指正错误及提出建议，我将及时修改、更新此 EFI。<br>
另外，如果有在 iOS 使用 Quantumult X 的用户，欢迎使用我的规则 [Stick Rules](https://github.com/GeQ1an/Rules/tree/master)，也欢迎 [点击此处](https://t.me/usestick) 订阅我的 Telegram 频道及时获取规则和 EFI 相关信息。
