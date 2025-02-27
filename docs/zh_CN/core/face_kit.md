# FACES Kit {docsify-ignore-all}

<img src="assets/img/product_pics/core/faces_kit/face_01.jpg" width="30%" height="30%" ><img src="assets/img/product_pics/core/faces_kit/face_02.jpg" width="30%" height="30%" ><img src="assets/img/product_pics/core/faces_kit/face_03.jpg" width="30%" height="30%" >


:memo:**[描述](#描述)**&nbsp;&nbsp;&nbsp;:bulb:**[上手指南](en/quick_start/m5core/m5stack_core_quick_start)**&nbsp;&nbsp;&nbsp;:octocat:**[例程](https://github.com/m5stack/M5Stack/tree/master/examples/Modules/FACES)**&nbsp;&nbsp;&nbsp;:electric_plug:**[原理图](https://github.com/m5stack/M5-Schematic/blob/master/Core/Basic/M5-Core-Schematic(20171206).pdf)**&nbsp;&nbsp;&nbsp;🛒**[购买链接](https://m5stack.com/collections/m5-core/products/m5go-iot-starter-kit-stem-education)**&nbsp;&nbsp;&nbsp;


## 描述

**FACES Kit** 是一系列功能面板的集合.套件内包含了三个常用的功能面板，"GameBoy（游戏键盘）"、"Calculator（计算器键盘）"、"QWERTY（输入全键盘）".内部集成**MEGA328**处理器，通过I2C通信协议（0x08）工作在从机模式下.根据需求去运用这3个不同的功能面板，进而实现用户与M5Core之间的人机交互.

### GameBoy Keyboard

如果你想用 M5Core 玩一些经典小游戏，那么使用GameBoy面板和 M5Core 会是完美的方案.你需要做的就是将游戏模拟器程序上传到 M5Core 上，并连接好 GameBoy 面板.连接图如下:

*下载游戏：https://docs.m5stack.com/#/zh_CN/quick_start/faces/gameboy_burn_a_nes_game*

<img src="assets/img/product_pics/core/faces_kit/face_05.jpg">

另外两个面板是计算器键盘和输入全键盘，你可以将它们运用在那些需要输入信息以及复杂控制的应用场景中.

### Calculator Keyboard

<img src="assets/img/product_pics/core/faces_kit/calculator.png">

### QWERTY Keyboard

<img src="assets/img/product_pics/core/faces_kit/face_04.jpg">

### FACE Charger

除了三个功能面板之外，套件内还提供了 Face 的专用充电座（充电座内置磁铁，能够稳定的吸附主机，并通过 POGO pin 对主机进行充电），杜邦线等配件.

<img src="assets/img/product_pics/core/faces_kit/charger.png">

关于本套件中的主机"Gray"的更多信息，请点击查看**Gray套件**

**注意：** 

新生产的M5Core更换了显示效果与可视角更加优质的屏幕，因此与旧版的Arduino库产生了一些兼容性问题，使用旧版程序库进行屏幕驱动时会产生反色显示的现象，您可以打开Arduino的库管理选项将您的M5Stack库升级至最新版本（0.2.8以后）来解决这个问题.

<img src="assets\img\product_pics\core\basic\lib_01.jpg" width="40%">
<br><br><br>
<img src="assets\img\product_pics\core\basic\lib_02.jpg" width="40%">

## 产品特性

- 5V 直流电源
- USB Type-C
- 基于 ESP32 开发
- 16 MByte flash(旧版：4 MByte flash)
- BMM150 + MPU6886
- 扬声器，按键x3，LCD屏幕（320 * 240），电源/复位按键x1
- 2.4G天线：Proant 440
- TF卡插槽（最大可拓展16GB）
- 电池总线母座和 650 mAh 锂电池
- 可拓展的引脚与接口
- Grove 接口
- M-Bus总线母座 & 引脚
- 开发平台 [UIFlow](http://flow.m5stack.com), [MicroPython](http://micropython.org/), [Arduino](http://www.arduino.cc)
- 产品尺寸：58.2mm x 54.2mm x 18.7mm
- 产品重量：264.6g


## 套件清单:

- 1x GRAY Controller
- 1x FACES 充电座
- 1x FACES 挂绳
- 1x 面板贴纸
- 3x FACES 键盘(GameBoy, Calculator, QWERTY)
- 8x 杜邦线
- 6x M3x10 螺丝
- 1x 六角螺丝扳手
- 1x Type-C USB

<img src="assets/img/product_pics/core/faces_kit/faces_kit.png">


## EasyLoader

<img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/EasyLoader_logo.png" width="100px" style="margin-top:20px">

<a href="https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/M5Core/Faces_kit/EasyLoader_Faces_kit.exe"><button type="button" class="btn btn-primary">点击下载EasyLoader</button></a>

>1.EasyLoader是一个简洁快速的程序烧录器，每一个产品页面里的EasyLoader都提供了一个与产品相关的案例程序.**(目前EasyLoader仅适用于Windows操作系统)**

>2.下载软件后，双击运行应用程序，将M5设备通过数据线连接至电脑,选择端口参数，点击 **"Burn"** 即可开始烧录

!>3.EasyLoader烧录前需要安装有CP210X（USB驱动程序），[点击此处查看驱动安装教程](zh_CN/related_documents/M5Burner#安装串口驱动)，在为Faces烧录固件前，请点击"Erase"进行一次内存擦除.


### 相关链接


-  **数据手册**

    - [ESP32](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_cn.pdf)
    - [MPU6886](https://github.com/m5stack/M5-Schematic/blob/master/datasheet/MPU-6886-000193%2Bv1.1_GHIC.PDF.pdf)
    - [BMM150](http://pdf1.alldatasheet.com/datasheet-pdf/view/608913/ETC2/BMM150.html)
    - [SH200Q](https://github.com/m5stack/M5-Schematic/blob/master/Core/SH200Q.pdf)

- **寄存器手册** 

    - [IP5306](https://github.com/m5stack/M5-Schematic/blob/master/Core/IIC_IP5306_REG_V1.4.pdf)


**IP5306充/放电，电压参数**

<table>
   <tr style="font-weight:bold;text-align:center" >
      <td>充电</td>
      <td><td>
      <td>放电</td>
   </tr>
   <tr>
      <td>0.00 ~ 3.40V -> 0%</td>
      <td><td>
      <td>4.20 ~ 4.07V -> 100%</td>
   </tr>
   <tr>
      <td>3.40 ~ 3.61V -> 25%</td>
      <td><td>
      <td>4.07 ~ 3.81V -> 75%</td>
   </tr>
   <tr>
      <td>3.61 ~ 3.88V -> 50%</td>
      <td><td>
      <td>3.81 ~ 3.55V -> 50%</td>
   </tr>
   <tr>
      <td>3.88 ~ 4.12V -> 75%</td>
      <td><td>
      <td>3.55 ~ 3.33V -> 25%</td>
   </tr>
   <tr>
      <td>4.12 ~   /   -> 100%</td>
      <td><td>
      <td>3.33 ~ 0.00V -> 0%</td>
   </tr>
</table>



## 管脚映射

**Mega328 ISP**下载接口Pin脚定义

<img src="assets\img\product_pics\app\mega328_isp.png" width="30%" height="30%">



**<mark>Notice：M5PORT 说明 </mark>**
*不同颜色的GROVE端口分别代表不同的功能.红色的PortA（21/22），为默认的I2C协议接口，黑色的PortB（26/36）, 支持DA/AD转换与信号总线通信.蓝色的PortC（16/17）, 支持Uart串口通信.在使用Unit进行功能拓展的时候，只需要匹配二者的端口的颜色，相应的进行连接即可正常使用.不仅提供简洁的硬件连接方式，还支持引脚的重映射.PortA（红色）被作为信号总线连接至是ESP32的GPIO21/22 ，没有AD通道转换方案，因此不能用作模拟输入使用.

- ADC1(8 通道 GPIO 32-39)
- ADC2(10 通道 GPIO 0，2，4，12-15，25-27)

使用AD读取功能:
1，使用杜邦线连接机身侧面的能够AD转换的引脚.
2，堆叠一个M5GO底座，使用其提供PortB.
3，使用PbHUB连接至PortA，拓展出6个PortB.
有关引脚分配和引脚重映射的更多信息，请查阅[ESP32数据手册](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_cn.pdf)

<br>
**<mark>注意3：Face Kit 出厂程序</mark>**<br>
出厂程序由于没有main.py文件，因此错误信息提示是正常的，并不意味着硬件问题,请放心使用. <br>
<img src="assets/img/product_pics/core/faces_kit/faces_kit_06.png" width="30%" hight="30%">

## 用户作品
- **[2048 Game with FACES Kit- Video](https://www.youtube.com/watch?v=ccEq0s7dU84)**
- **[2048 Game with FACES Kit- Source Code](https://github.com/phillowcompiler/2048_M5Stack)**