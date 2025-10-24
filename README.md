---
#  探索在pc上安装macos Tahoe
### A-path-to-exploring-installation-macOS-tahoe-EFI_ASUS_ROG-Z690_INTEL12400_RX6600
---
## 闲来无事，想着既然macOS tahoe为最后一个支持Intel芯片的大版本系统，索性花时间自己安装一下，优化好后，以后稳定使用，再不用折腾以追求更新的系统更新。此前安装过多次黑苹果系统，都是浅尝辄止，从搜寻安装镜像到搜索相近EFI文件，尝试安装，以尝鲜为主要目的，并不以稳定使用为前提，故大多知其然，不知其所以然。因不同系统版本、不同硬件、不同错误之于网上有太多的鱼龙混杂的教程，因此想自行实践配出匹配自己使用硬件的EFI,并长期使用。具体过程、当中遇到的坑及相应方法，记录如下：
## 一、生成dmg安装镜像
### 1.下载macos原版pkg:
####  推荐：[https://mrmacintosh.com]
  （用中文搜索出来的大多是付费下载或各种龟速网盘，且版本不全，此网站不可不谓之太好用了，极速下载且版本齐全、一目了然。国人把众多国外免费分享、用爱发电的开源内容都视为可圈钱的资源，只能说吃相难看，还说明因为各种各样的原因，就是存在信息差让一些人得利）。
#### 另一种方法为使用gibMacOS下载：[https://github.com/aeonme/gibMacOS]
### 2.制作dmg安装镜像文件：
#### 在尝试后发现，如果没有mac，需要先安装一版黑苹果（这一步用到了此前下载的可以安装的dmg包），才能通过macos使用官方教程制作dmg镜像：
  [https://support.apple.com/zh-cn/101578]
#### 以制作MacOS_tahole为例：
  在mac中打开磁盘工具，选择“空白镜像”新建了一个名为26的dmg镜像文件到桌面上，参照官网的教程。使用如下代码制作dmg安装文件：
  ```
sudo /Applications/Install\ macOS\ Tahoe.app/Contents/Resources/createinstallmedia --volume /Volumes/26 
  ```
  在生成后使用occ或其他的可以挂载磁盘的软件，挂载生成的dmg文件，里面即已存在名为EFI的分区，将编辑配置好的EFI放置其中，再推出此dmg，即制作完成属于自己电脑的专属安装镜像文件。
## 二、定制EFI文件
####  参考学习：
####  dortania大神的安装指南，几乎囊括了所有安装教程及避坑指南：
#### [https://dortania.github.io]
####  [https://github.com/dortania/OpenCore-Install-Guide]
####  最新编译的驱动及OC：
####  [https://dortania.github.io/builds/]
### 1.使用OpCore-Simplify定制生成EFI
  [https://github.com/lzhoang2801/OpCore-Simplify]
### 2.使用USBMap定制usb，并生成usb驱动
  [https://github.com/corpnewt/USBMap]
### 3.生成dmg安装镜像，使用balenaEtcher写入u盘：
 [https://etcher.balena.io]
 定制过程需要仔细学习各个工具的说明，尤其是对于像tahoe这样的大版本更新系统，有很多坑在主页均有所提示，如：OpCore-Simplify自动生成的我的机型不支持tahoe，usbmap定制后无需使用其他usb驱动等等，免驱显卡无需开启-lilubetaall等，可避免很多安装过程中出现的奇奇怪怪的bug，与其头痛医头、脚痛医脚，不如在开始制作安装时就针对性避免，其实是节约了时间。
## 三、安装完成后的优化
###  ·无线网卡的驱动及使用：
  使用OpCore-Simplify定制时会指引提示Tahoe只用通过itlwm+HeliPort使用无线网卡，因此使用CChenxiiiii（小孩哥）做的轮子，可以无感使用WiFi：[https://github.com/CChenxiiiii/CCToolBox]
###  ·cpu睿频驱动及使用：
  依然可使用上面小孩哥的软件，但是注意，Tahoe无法使用如iMac Pro的机型，我使用的是mac7,1也就是macpro 2019的机型，因此搜索教程：[https://bbs.pcbeta.com/viewthread-1974294-1-1.html]，
###  需要打开AppleXcpmForceBoost这个选项，可以达到12400多核4.0 单核4.4，这时cpu跑分正常了。

---
###  至此，黑苹果系统基本完成配置，除了无线网络链接略受限以外，其余的都无问题，性能也能完全释放。12400单核约为m1水平，多核约为m1pro.
###
---
  <img width="1436" height="899" alt="截屏2025-10-22 23 43 28" src="https://github.com/user-attachments/assets/ea25b248-291f-4b74-bffc-9a57059c7df5" />
<img width="1436" height="899" alt="截屏2025-10-22 23 47 09" src="https://github.com/user-attachments/assets/957ebef7-8b9b-483c-8050-4d8ea69ae3f8" />
<img width="1436" height="899" alt="截屏2025-10-22 23 49 14" src="https://github.com/user-attachments/assets/d1dac67d-4d49-450d-9753-805e79177910" />

# 贡献列表
- [Coceki](https://github.com/Coceki/FunHouse-F10-MPro-Ice-Lake-Hackintosh-Tahoe?tab=readme-ov-file)看到此人的链接，萌生此次实践的想法，也感谢其贡献列表，省去了很多查找资料的时间。
- [Apple](https://apple.com) 的macOS
- [Acidanthera](https://github.com/acidanthera) 的OpenCore项目与Kexts
- [Dortania](https://github.com/dortania) 提供了详细的教程参考
- [lzhoang2801](https://github.com/lzhoang2801) OpCore Simplify帮助节省了很多前期时间
- [wxjiyc](https://github.com/wxjiyc/) 提供了驱动触控板的代码思路
- [corpnewt](https://github.com/corpnewt/USBMap) 提供了适用于Tahoe的USB定制工具
- [CChenxiiiii](https://github.com/CChenxiiiii/CCToolBox)小孩哥的工具箱，挺好用的，后生可畏
