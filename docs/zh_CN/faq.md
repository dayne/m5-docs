# 常见问题解答 {docsify-ignore-all}

**[M5CORE](#M5CORE-Question)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[UNIT](#UNIT-Question)**

<!-- **[主控](#主控)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[模块](#模块)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[底座](#底座)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[单元](#单元)** -->


## M5CORE 相关问题

- **Q1: 不同的M5主机之间有什么区别？**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q1">查看解答</button>
  <div id="Q1" class="collapse">
    这些主控主要区别在内部硬件配置和套件搭配上，从基础版到升级版，分别是增加了姿态传感器 MPU9250和加大了 RAM 和 FLASH，具体区别请访问<a href="https://github.com/m5stack/M5-Schematic/blob/master/Core/hardware_difference_between_cores_zh_CN.md">这里</a>

<img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_table/core_comparison/core_main_comparison_04_zh_CN.png">

<img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_table/core_comparison/core_main_comparison_05_zh_CN.png">
  </div>
</div>


- **Q2: 如何关闭 M5Core 的喇叭功能？**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q2">查看解答</button>
  <div id="Q2" class="collapse">
    在 Arduino 程序的 Setup(){} 中执行以下语句

    ```arduino
    dacWrite(M5STACKFIRE_SPEAKER_PIN, 0);
    ```
  </div>
</div>

- **Q3: 有些模块与 M5Core 堆叠之后不能下载程序，比如 USB 模块与 M5Core 堆叠**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q3">查看解答</button>
  <div id="Q3" class="collapse">
    可能是堆叠之后，M5-Bus 总线上的引脚 GPIO0 与 M5Core 接触不太好。这种情况下，在下载程序的时候，GPIO0 理应会一直保持低电平的，可是因为接触不好，GPIO0 不能一直保持低电平，所以下载失败。

    解决方案：在下载过程中，手动让 GPIO0 连接 GND，保证足够长时间拉低。
  </div>
</div>


- **Q4: M5GO 底座堆叠了 M5Core 之后，M5Core 不能开机，可是测试了底座电池满电。**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q4">查看解答</button>
  <div id="Q4" class="collapse">
    可能是堆叠之后，底座上的 M5-Bus 总线上的左下角的引脚 BATTERY 与 M5Core 接触不太好，这是生产时焊接位置偏了导致的。总线排针焊接位置稍微偏了一些之后，容易出现 BATTERY 引脚与 M5Core 接触不好。

    解决方案：重新焊接 M5-Bus 总线排针，排针位置必须严格与焊盘位置吻合。
  </div>
</div>

- **Q5: 有的电脑虽然连接上了主控，可是仍然无法使用 Arduino IDE、ESPFlashDownloadTool 或 M5Burner 来烧录程序。例如下图使用 Arduino IDE 的时候的情况。**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q5">查看解答</button>
  <div id="Q5" class="collapse">
    <img src="assets/img/faq/faq_03.png">
    原因和解决方案：可能是因为这些串口的供电电流不够大，需要在主控中的 RST 引脚和 GND 引脚之间接入电容 ( 电容值是比0.1uF大的 )，或者在下载程序的时候，将 GPIO 0 连接到 GND，使得 GPIO 0 能持续足够的低电平。

<img src="assets/img/faq/faq_05.png" width="80%" height="80%">

<img src="assets/img/faq/faq_06.png" width="80%" height="80%">

<img src="assets/img/faq/faq_07.png" width="100%" height="100%">
  </div>
</div>

- **Q6: ESP32 有哪些特殊的 GPIO 管脚需要注意？**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q6">查看解答</button>
  <div id="Q6" class="collapse">
    ESP32 有 34 个 GPIO 管脚，其中 GPIO 34-39 仅用作输入，不能作为输出，其他的既可以作为输入又可以作为输出管脚。
  </div>
</div>


- **Q7: 为什么带 MPU9250 的 Stick 烧录了出厂固件之后，按按键 A，结果显示 "No"，即 "不存在9250"。**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q7">查看解答</button>
  <div id="Q7" class="collapse">
    重启这个 Stick，就可以显示。因为读取 MPU9250 的代码放置在出厂程序的 setup() 函数中，开机只执行一次，所以重启，让 Stick 再检测一次 MPU9250。
  </div>
</div>

- **Q8: 烧录FACES Kit 出厂程序后，屏幕上显示如下的错误**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q8">查看解答</button>
  <div id="Q8" class="collapse">
    <img src="assets/img/faq/faq_08_01.png" width="100%" height="100%">
    这是正常现象，因为程序里面有没main.py文件，所以才有这个警告。
    
  </div>
</div>

- **Q9: M5stickC 无法开机.**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q9">answer</button>
  <div id="Q9" class="collapse">
    <img src="assets/img/faq/m5stickc_05.jpg" width="50%" height="50%">

  M5StickC存在一个问题，即电池处于低电量情况下，容易发生无法开机的现象.

  以下操作能够使设备恢复正常：1，将G0短接到3V3。 2.插入USB线。 3，屏幕亮起后停止短接，USB继续为设备充电. 
  </div>
</div>


- **Q10: M5stickC 无法识别端口（COM）.**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#Q10">answer</button>
  <div id="Q10" class="collapse">

  M5StickC仅支持WIN10&Linux&MAC免驱，其余操作系统则需要用户自行安装驱动程序.

  安装步骤：1，点击下方链接，下载驱动安装包. 2.连接设备，并打开电脑设备管理器端口选项。 3，右键点击未能识别的设备，进行手动更新. 

  <a href="https://www.ftdichip.com/Drivers/VCP.htm">驱动下载连接</a>

  </div>
</div>


## UNIT 相关问题

- **Q1: M5Stack 的多款摄像头 Unit 之间有什么区别？**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#U-Q1">查看解答</button>
  <div id="U-Q1" class="collapse">
    这些摄像头主要区别在于一些管脚 (OV2640-SIOD、OV2640-VSYNC、GROVE 接口)、镜头类型、有无 PSRAM，具体区别请访问<a href="https://shimo.im/sheets/gP96C8YTdyjGgKQC/e2041">这里</a>

<img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_table/camera_comparison/camera_comparison_zh_CN.png">
  </div>
</div>


- **Q2: 摄像头通过 WIFI 传输图像给手机，能传输多远？**

<div class="container">
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#U-Q2">查看解答</button>
  <div id="U-Q2" class="collapse">
    经过测试，在室内使用 M5Camera 能传输 20 米左右。
  </div>
</div>