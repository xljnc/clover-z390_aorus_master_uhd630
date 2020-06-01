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
4. 此主板有个问题，就是板载只有一个HDMI接口，没有DP接口。而Coffeelake的uhd630如果驱动不成功，可以进入系统，
但是显存只有7mb。通过教程
