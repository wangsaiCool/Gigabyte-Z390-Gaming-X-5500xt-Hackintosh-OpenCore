# Gigabyte-Z390-Gaming-X-9600K-5500xt-Hackintosh-OpenCore
Gigabyte-Z390-Gaming-X + Intel i5 9600K + AMD Radeon RX 5500XT 8 GB 



# 需求
在组装的台式机电脑上，使用OpenCore的方式安装黑苹果 MacOS 10.15.* 下文是安装教程。

# 目标

|目标|进度|
--|--
|显卡正常   | 免驱，正常|
|网卡正常   | 免驱，正常|
|蓝牙正常   | 免驱，正常|
|USB内建    | Done|
|睡眠正常   | Done|
|变频正常   | Done|
|AIRDROP正常| Done|
|声卡正常   | Done|
|随航正常   | Done|
|妙控板2代  | 免驱，正常|
|核显和独显驱动正常 | Done|
|鼠标拖动声音滑块会卡顿一下，但使用键盘调音量没问题  |==TODO==|


# 机器配置清单
|类型|型号|购买价格|链接|
--|-- |-- |--
|主板|Gigabyte Z390 Gaming X|999 |https://u.jd.com/ng5IUG|
|cpu|i5 9600k|1599 |https://u.jd.com/BRWE7W|
|显卡|蓝宝石 5500XT|1549 |https://u.jd.com/Lgx44B|
|网卡&蓝牙|BCM94360CD|270 |某宝一大堆，记得买4天线的 |
|内存|海盗船 DDR4 3200 16G×2|948.5 |https://u.jd.com/l9ZuYL|
|硬盘|西数黑盘 SN750 M.2 512G|599 |https://u.jd.com/X3T7wk|
|显示器|LG  27UL650 4k|2499 |https://u.jd.com/RzIzfj|
|机箱|MasterBox Q500L | 259 | https://u.jd.com/xBPsg7|
|CPU散热器|九州风神大霜塔| 179|https://u.jd.com/xndQfK|
|机箱风扇|先马（SAMA）游戏风暴 12CM无光*2|19.8 |https://u.jd.com/dc8JAp|
|电源| 安钛克(Antec)HCG650金牌全模|579|https://u.jd.com/cs8WeW|
|妙控板|妙控板2代|973|https://u.jd.com/ql4yXO|

# 预览
![detail](https://note.youdao.com/yws/api/personal/file/WEBbe16f67f213f71bec28cb93a601fa739?method=download&shareKey=0e45f63969983f8c1d422b13b364297e)

![intel power gadget](https://note.youdao.com/yws/api/personal/file/WEBf6da75e9d6e29330b68f6430808d2e1a?method=download&shareKey=1968eb801a850adeef5dcb44e2c20336)

# 安装步骤

## Step1，准备镜像

两个镜像二选一即可，我使用的是 *镜像1【Len's 的镜像】*
#### 镜像1，【Len's 的镜像】
> Len's 镜像介绍，http://bbs.pcbeta.com/viewthread-1858946-1-1.html   
> 文件校验值如下:  
> -- CRC32: D64AA696  
> -- MD5: 97684383A7C7F1036B9E7DDFD9B665AC
> SHA-1: 2F25E80B70A175944BEC8565B1A2EE8B2FB575FA
>  - 1，[百度网盘链接]，https://pan.baidu.com/s/1WLiOnchDZ-CHy_rgWXdhLg  提取码: deti
>  - 1'，[百度网盘备用链接]，https://pan.baidu.com/s/1PWqb9zTl0a2DseqIcsnvBQ 提取码: idgj
>  - 2，[天翼云盘]，https://cloud.189.cn/t/qM3YZnRjUVjy
 
#### 镜像2，【黑果小兵的镜像】
> 镜像名称：macOS Catalina 10.15.5 19F101   
> 镜像介绍：https://blog.daliansky.net/  
> 文件校验值，MD5校验值：9a6e6bca1882f6791bafa4d6b45c28ce   
> 下载地址：  
> - 1，[天翼云盘]： https://cloud.189.cn/t/FfQRjyzeEF3i  
> - 2，[OneDrive下载]：http://suo.im/5wzhYq  

## Step2，BIOS设置和制作镜像
- 参考B站大神大头蔡的视频(切记z390系列主板，需要替换一个文件)：
- https://www.bilibili.com/video/BV1SQ4y1A73s
- 视频中提到的，需要更改的BIOS如下：
> Tweaker -> Advanced CPU -> vt-d -> Disable  
> Boot -> CSM -> Disable   
> Setting -> IO Ports -> Internal Graphics -> Disable  
> Tweaker -> X.M.P -> profile1  
> Setting -> IO Ports -> above 4G Decoding -> Enbale  
> Setting -> SATA and RST config -> SATA mode -> AHCI  
> Setting -> USB config -> XHC2 hand off -> Enable

配置完成之后，重启，进入BIOS界面，检查配置结果：重启后，这里应该只有UEFI启动项条目

## Step3，安装镜像
- 安装步骤文字版：  

> - ~~0 进入win系统，打开DiskGenius格式化要安装Mac的硬盘，格式化为NTFS~~（这里是为了彻底格式化，其实这一步也可以不用做）；
> - 1 插入做好的Mac U盘，重启电脑，选择从U盘启动
> - 2 在Mac安装界面，选择options  -> boot args中新增agdpmod=pikera -> return -> 选择boot macOS install from Len's ** ,跑完代码之后进入安装界面 -> 选择简体中文，进入实用工具界面；
> - 3 选择磁盘工具  -> 左上角，显示所有磁盘 -> 选中磁盘 -> 抹掉 -> 格式选择APFS，方案GUID分区图，名称Macintosh HD -> 抹掉，之后退出磁盘工具。
> - --3.1，若要从备份进行恢复的话，选择从timeMachine备份进行恢复  
*++[如果无法识别TimeMachine，把移动硬盘换一个USB口重新尝试一下]++*
> - --3.2，全新安装的话：  
*-- step1，在实用工具界面，选择 安装MacOS -> 一路同意...  ->  会进入选择磁盘项 -> 开始安装 -> 安装结束会重启，开始step2；  
-- step2，继续选择从U盘启动，重复【选择options  -> boot args中新增agdpmod=pikera启动参数 ，回到引导界面 -≥ Boot macOS intall from Macintosh HD -≥ 进入跑代码界面，会继续重启 -≥ 重启后，继续选择从U盘启动】，重复step2的步骤，总共需要重复3次。  
-- step3，最后会进入初始化界面，可以进入正式安装了*。

- 安装步骤视频版，https://www.bilibili.com/video/BV1Rg4y1B7tE
- 安装过程遇见的问题：
```
 -- 1-问题1：遇见跑完代码直接黑屏  
 -- 1-解决方法，在启动项注入：agdpmod=pikera  
 -- 2-问题2：安装后重启报错 Error：Aborted returned from boot.efi  
 -- 2-解决方法1：在boot args中注入:agdpmod=pikera，重启  
 -- 2-解决方法2：如果还不行看下这篇文章  
 https://www.jianshu.com/p/342b322e3841 ，  
 http://imacos.top/2020/03/28/0154/  
设置为enable或者disable多试几次  
 -- 2-解决方法3：如果还不行，那么应该是Step2中的文件没有被替换
```
## Step4，黑苹果安装之后的简单配置
- 参考，https://www.bilibili.com/video/BV1og4y1B7Qa


## Step5，OC引导文件配置
- 操作步骤文字版：  
-- step1，使用0.5.9版本的OCC挂载EFI分区 -> 将下面的==EFI==文件copy至EFI   
-- step2，使用OCC打开config.plist -> NVRAM -> 去掉cfg**lock的勾  
-- step3，进入系统之后，鼠标和键盘失灵的解决方法， 在选择OpenCore选择机型的时候，选择iMac19,1 ,不要选择iMac pro  
> 我的==EFI==配置文件，https://pan.baidu.com/s/1ttClcdp4kx8CcBIViY6DbA  
> 提取码：mfxs


- 操作步骤视频版，https://www.bilibili.com/video/BV1BK4y147hX   
```
-- 若能在github找到类似的硬件，可以直接使用efi文件  
-- 另外，先不要解锁 CFG，后面会有更简单的方法
```

```
-- 切记，记得自己生成新的三码（参考上述视频）  
-- 切记，这里需要使用OpenCore Configuration  0.5.9版本 ，其他的可能会有问题
-- 如果配置完，重启失败的话，可能是NVRAM下的 cfg***lock的勾选要取消
```

## Step6， 硬盘引导
- 参考，https://www.bilibili.com/video/BV16C4y187ta
- 遇见的问题：  
-- 问题1，配置完成，重启后，一直白苹果  
-- 解决方式：  
----step1，在OpenCore Configuration里面 boot args添加-v  
----step2，重启，屏幕会有根据信息，去这里找原因：http://imacos.top/2020/03/28/0154/  

## Step7，无法使用AirDrop
- 因为缺少AirportBrcmFixup.kext  
- 解决方法，从这里下载 https://github.com/acidanthera/AirportBrcmFixup/releases ,并且使用OC进行配置

## Step8，配置开机界面的主题
- 下载主题，http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1853170&highlight=oc%D6%F7%CC%E2
- 将icons放置到oc目录下，替换opencore.efi
- 重启，可以观察到效果

## Step9，解锁CFG  
- 操作前，记得备份bios到U盘（插入U盘，按F12进入BIOS，选择QFlash，根据提示就能备份了，建议备份一下）
- 解锁操作步骤：

> - 1，进入WIN系统插入另一个U盘，格式化为FAT32并命名为EFI，进入U盘新建文件夹EFI/BOOT  
> - 2，将BOOTx64.efi复制到BOOT路径下
> - 3，重启按F12，选择从刚才的U盘启动，进入解锁的命令终端界面
> - 4，查询CFG锁的状态命令：setup_var 0x5c1（屏幕输出的内容中，如果对应的内容为0x01说明没有解锁，如果为0x00说明已经解锁）
> - 5，解锁命令：setup_var 0x5c1 0x00

- 验证结果：

> - 1，重启电脑
> - 2，打开hackinTool ≥≥ 工具项 ≥≥ appleinterInfo查看，可以查到CFG_lock的值为0

- 收尾：
> - 1，取消config.plist中的cfg**lock选项（在NVRAM选项中，共有2个需要勾选）
> - 2，重启电脑，可以正常进入系统

- 视频操作步骤参考，www.bilibili.com/video/BV1ka4y1x7Z2/
- 用到的工具打包，链接: https://pan.baidu.com/s/1yDaEcd1PDhSTxwW3nCLnvA 提取码: zi1a

## Step10，问题整理：
- 每次启动logo画面读条一半然后黑屏，四五秒后进登录页，为什么黑屏那一下？
- 是引导工具比如clover模拟的引导，转换成了macos自身的引导，黑一下是避免不了的。

## Step11，查看CPU性能的intel插件
- https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html


## Step12，修复双系统下，win时间不准的问题
- 进入win下操作
- 链接: https://pan.baidu.com/s/1ig_yXWdTkLWy-U6W00QGkQ 提取码: sdrh

## Step13，Final Cut Pro软件和Logic Pro X
- 链接: https://pan.baidu.com/s/1WplzmbYiVa61fxqYbAyGsw  密码: ogfj  
- 链接: https://pan.baidu.com/s/148i16FgwYu9l379V58nBBA  密码: g1jq

## Step14，开启核显加速
- 目的：为了使用原生电源管理、系统会更稳定，稳定压倒一切
- step1，删除以前注入的核显id
> - 1，使用OCC(0.5.9)打开EFI分区下的 config.plist -> Device Properties  -> 删除 PciRoot 0x0/Pci 0X2 0x0（子选项只有** platform **）
> - 2，添加启动参数，使用OCC配置 NVRAM -> boot args -> 新增igfxfw=2

- step2，配置WhatEverGreen(WEG)
> - 1，下载最新WhatEverGreen，https://github.com/acidanthera/WhateverGreen/releases/tag/1.4.2  
> - 2，使用OCC打开EFI的config.plist，替换现在使用的WEG（直接拖入覆盖原来的WEG即可）

- step3，重启电脑，验证生效
> 打开intel powerGadget，查看GFX选项已经可以稳定在1.2Ghz左右


# TODO 
## TODO-1, 使用鼠标调节音量的时候，按钮会卡顿
解决方式，需要关闭主板的串口。由于技嘉z390主板bios界面不能关闭serial port，可以通过刷bios的方式解决。 
 
========== ==到这里安装黑苹果系统就完成了，可以愉快的使用了== ===================   

========== ==我是分割线== =====================================================

========== ==下面是从时间机器恢复备份的的步骤==  ================================


# 从TimeMachine恢复系统 
## 重刷BIOS
- step1，将U盘格式化为FAT32（准备另一个U盘，不要使用Mac U盘）
- step2，将../bakupMacEFI_20201003/mb_bios_z390-gaming-x_f9-官方原版/下的文件Z390GX.F9，copy至FAT32的U盘
- step3，从U盘启动，使用QFlash将BIOS刷入主板


## 格式化硬盘
 - step0，插入做好的Mac U盘，重启电脑，选择从U盘启动  
 - step1，在Mac安装界面，选择options  -> boot args中新增agdpmod=pikera -> return -> 选择boot macOS install from Len's ** ,跑完代码之后进入安装界面 -> 选择简体中文，进入实用工具界面   
 - step2，格式化：选择磁盘工具，显示所有磁盘 -> 选中要装系统的盘 -> 抹掉 -> 命名为Macintosh HD，APFS，GUID分区图  
 - step3，格式化完成，退出磁盘工具
 - ~~step4，格式化完成之后，重启电脑进入win系统，用Diskgenius查看这个磁盘是否还存在efi分区：  
-- 如果存在，则用diskgenius格式化这个磁盘，可以格式化为任意合适。之后，参照“格式化硬盘”，重新格式化磁盘。  
-- 如果不存在efi分区，则不需要特别操作。~~ （不是必须的）


## 恢复系统操作
- step1 回到实用工具界面，选择从timeMachine备份进行恢复  
*++[如果无法识别TimeMachine，把移动硬盘换一个USB2.0口重试]++*  
- step2 恢复完成之后，配置EFI【参考 **《OC引导文件配置》**】
- step3 配置 cfg【参考 **《解锁CFG》**】
- step4 洗白，即生成三码
- step5 【开启 **《开启核显加速》** 】


## Mac系统简单配置
- 打开随航、打开TimeMachine备份、登录iCloud
- 恢复系统完成
