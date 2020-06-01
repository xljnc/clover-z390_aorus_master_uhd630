# clover-z390_aorus_master_uhd630
## black🍎 install with gigabyte z390 aorus master and intel graphic uhd 630
黑🍎安装记录，也不是什么专业教程。只是花了几天研究了一下，记录下自己安装时遇到的问题。
依然小白一个，只是误打误撞成功了，希望能帮到大家。
首先感谢黑果小兵，里面有很多教程。地址：https://blog.daliansky.net/
## 系统: macos x mojave 10.14.6
## 硬件列表：
* cpu: i9-9900k (coffee lake)
* 主板：技嘉（gigabyte） z390 aorus master（bios version：F8）
* 硬盘：三星 970 evo plus（需要更新到最新固件）
* 核显：intel graphic uhd 630
* 独显：gtx1660ti(无法驱动) 
* 声卡：板载Realtek ALC1220-VB
## 驱动情况：
1. 声卡驱动 成功
2. 独显驱动 失败，我把1660ti拔掉了，据说在启动参数上加上－wegnoegpu可以实现，
但是我一直不成功，只要连着显卡就不能进入系统。我用的是集显。据说AMD显卡免驱。
3. 集显驱动 成功，需要一定设置
4. 声卡驱动 成功，使用applealc + lilu 
5. 有线网卡 成功
6. 无限网卡 未测试，我一直没使用
7. 蓝牙驱动 未测试
## 流程以及遇到的坑：
1. 首先三星 970 evo plus在老版本固件下，安装完系统很卡（我没测试，我安装前直接更新到最新固件）。
2. 开普勒GK104/GK107/GK110核心的在Mojave里原生驱动，开普勒GK106/GK208核心的在10.12.6+的系统里花屏闪屏，
因此无法驱动1660ti，有需要请上AMD显卡，我直接用了核显uhd630
3. 主板 技嘉z390 aorus master，bios更新到了F8.安装前bios需要一定bios设置，具体请百度。
4. 此主板有个问题，就是板载只有一个HDMI接口，没有DP接口。而Coffeelake的uhd630如果驱动不成功，可以连hdmi进入系统，
但是显存只有7mb。通过黑果小兵教程https://blog.daliansky.net/Intel-core-display-platformID-finishing.html
注入正确的platform ID，则驱动成功，但是会黑屏（默认DP输出，但是没有板载dp口）。所以需要按照教程
https://blog.daliansky.net/Tutorial-Using-Hackintool-to-open-the-correct-pose-of-the-8th-generation-core-display-HDMI-or-DVI-output.html 设置HDMI输出。然而我一直没成功。。。我后来是用的黑果小兵镜像里的config uhd630 hdmi 直接成功驱动。
5. 板载声卡无法直接驱动，需要通过applealc + lilu注入id，我用的id是16.
6. 安装时日志提示Error allocating 0x11c8d pages at 0x0000 alloc type 2,参考教程https://blog.daliansky.net/Slide-value-acquisition-and-calculation.html 计算slide值，然后在启动参数boot args添加：slide=1（我的是1，每个人不同）
7. 安装时提示"MacOS Mojave应用程序副本已损坏",请拔掉网线，然后打开终端，使用命令 date  053008102019.20
格式是月 日 时 分 年 秒。然后就可以安装了。
8. 我是win10+黑🍎双系统，所以需要diskgenius来创建一个efi分区并且大小大于200m，切记一定要做这一步。我第一次安装不知道没做，
然后win10的引导没了，无法进入win10，无法修复。可以参考教程https://blog.csdn.net/qq_35379989/article/details/83387358

