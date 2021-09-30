# 使用 YADAN Board  
  
本章将介绍如何把 YADAN SoC 或 PULPino SoC 部署到我们的 YADAN Board 中，使其变成一块类似 Arduino UNO 的嵌入式开发板。部署完成后，配合第三章中在 Arduino IDE 中配置好的环境，我们即可像使用 Arduino 一样便捷地在 YADAN Board 上开发嵌入式软件。  
  
## 部署 SoC 至 FPGA  

综合好的 YADAN SoC 的 `.bit` 文件为 `Yadan.bit`，PULPino SoC 的为 `pulpino_zeroriscy.bit`，分别可在下边两个链接中找到。  
  
+ YADAN SoC: [https://gitee.com/verimake/yadansoc/tree/master/prj](https://gitee.com/verimake/yadansoc/tree/master/prj)
+ PULPino SoC: [https://pan.baidu.com/s/1uzZ-Ic4XPclwRXgk5f-Z_g](https://pan.baidu.com/s/1uzZ-Ic4XPclwRXgk5f-Z_g) (提取码: 3005, 在 “Zeroriscy内核开发工具” 文件夹中)
  
打开安装好的 TD 软件，点击如图 4.1 所示的按钮打开下载工具。
  
**<center>![图 4.1 TD 软件中打开下载工具的按钮](imgs/img_04_01.png)  
图 4.1 TD 软件中打开下载工具的按钮</center>** 
  
打开的下载工具的界面如图 4.2。  
**<center>![图 4.2 下载工具的界面](imgs/img_04_02.png)  
图 4.2 下载工具的界面</center>** 
  
将 YADAN Board 通过 Type-C USB 线与 PC 机相连，下载工具中原先显示 `No hardware` 的下拉框就会自动更新为 `EG4S20NG88`（如果加载不了需要检查下载器驱动是否正确安装，详情见[第 3.3 节](chap3.html#id3)）。加载成功开发板后，界面如图 4.3 所示。  
  
**<center>![图 4.3 下载工具加载成功开发板后的界面](imgs/img_04_03.png)  
图 4.3 下载工具加载成功开发板后的界面</center>** 
  
然后点击如图 4 所示的 `Add` 按钮，添加你想部署的 SoC 的 `.bit` 文件。
  
**<center>![图 4.4 下载工具中的 `Add` 按钮](imgs/img_04_04.png)  
图 4.4 下载工具中的 `Add` 按钮</center>**
  
添加 `.bit` 文件完成后，可以看到文件的相关信息，包含该文件适用的芯片型号、封装、生成时间等，如图 4.5 为例。  
  
**<center>![图 4.5 显示的 `Yadan.bit` 的文件信息（如果用 PULPino，也能看到类似的内容）](imgs/img_04_05.png)  
图 4.5 显示的 `Yadan.bit` 的文件信息（如果用 PULPino，也能看到类似的内容）</center>**

`Mode Selection` 中可以选择下载模式，默认的下载模式为 `JTAG` 模式，适用于调试，但配置会在掉电后丢失。如果我们希望下次上电后 FPGA 能自动加载配置，则需要把配置下载到 FPGA 的配置芯片外置的 Flash 中，即我们需要选择下载模式为 `PROGRAM FLASH` 模式。下载速度默认为 1Mbps，我们可根据电脑和线材条件自由选择，但如果下载失败，需尝试降低下载速度再重新下载。选择下载模式的下拉框如图 4.6 所示。

**<center>![图 4.6 选择下载模式的下拉框](imgs/img_04_06.png)  
图 4.6 选择下载模式的下拉框</center>**
  
在该模式下载完成后，开发板每次上电时，会先将 Flash 中存储的配置数据自动加载到 FPGA 中。  
  
## 使用 Arduino IDE 开发应用程序  
  
在[第 3.4 节](chap3.html#arduino-ide-yadan-board)，我们介绍了如何安装与配置 Arduino IDE 和 YADAN Board 开发板工具包。本节将介绍如何使用 Arduino IDE 给开发板开发嵌入式软件。
  
首先，使用 Micro-USB 线将部署好 SoC 的开发板连接至电脑，电脑会读取到一个 UART 串口，我们可在设备管理器中看到名为 `USB-SERIAL CH340` 的这个串口，括号内即为该串口的 COM 号，如图 4.7 为例。如果没有看到串口号或显示未知设备，需要在百度网盘中或[沁恒官网的对应页面](http://www.wch.cn/products/CH340.html)下载 CH340 的驱动程序并安装。  
  
**<center>![图 4.7 在设备管理器中查询串口的 COM 号（不同电脑会分配不同的编号）](imgs/img_04_07.png)  
图 4.7 在设备管理器中查询串口的 COM 号（不同电脑会分配不同的编号）</center>**

打开 Arduino IDE，根据之前部署的 SoC，在 `Tools -> Board` 中选择 `YADAN Board (VeriMake)` 中的 `YADAN` 或 `Zero-risky`。然后根据刚才查询到的 COM 号，然后选择 Port 为刚刚查询的串口号，如图 4.8 所示。  

**<center>![图 4.8 选择开发板的串口号（不同电脑会分配不同的编号）](imgs/img_04_08.png)  
图 4.8 选择开发板的串口号（不同电脑会分配不同的编号）</center>**
  
接下来就可以使用 Arduino 语言来开发嵌入式软件了，Arduino 语言的语法请参考 Arduino 官网的 [Language Reference](https://www.arduino.cc/reference/en/)。不过要注意的是，YADAN SoC 或者 PULPino SoC 暂时还不支持所有的 Arduino 函数，例如 Analog I/O 里的 `analogRead()` `analogReference()` 等与模数转换器 (Analog-to-Digital Converter, ADC) 相关的内容暂时还不可用（因为目前本文档中所述的 YADAN SoC 或者 PULPino SoC 还没有实例化 ADC 端口，需修改 SoC 添加外设来支持，但这部分不在嵌入式软件的教学内）。此外还需注意的是，原版 Arduino 是以 AVR 单片机为平台来开发的，但是我们使用的是 RISC-V 指令集的 SoC，所以不一定百分百兼容所有的 Arduino 函数。  
  
**<center>![图 4.9 Arduino 官网的 Language Reference](imgs/img_04_09.png)  
图 4.9 Arduino 官网的 Language Reference</center>**
  
我们可以参考 Arduino 的[基础示例](https://www.arduino.cc/en/Tutorial/BuiltInExamples)，编写一个让 LED 闪烁的简单程序来了解开发的整个流程。首先先填入下列代码（这份代码也可以在 Arduino IDE 的 `File -> Examples -> 01.Basics -> Blink` 中找到）
```
/*
  Blink
  Turns an LED on for one second, then off for one second, repeatedly.
  This example code is in the public domain: http://www.arduino.cc/en/Tutorial/Blink
*/

// the setup function runs once when you press reset or power the board
void setup() 
{
    // initialize digital pin LED_BUILTIN as an output.
    pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() 
{
    digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
    delay(1000);                       // wait for a second
    digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
    delay(1000);                       // wait for a second
}
```
  
代码中的 `LED_BUILTIN` 对应开发板上 GPIO 的第 13 号引脚，该引脚在电路中连接了一个 LED（原理图可参考[第 1.2.2 节](chap1.html#led)），这份代码将实现让这个 LED 亮一秒、灭一秒的无限循环。我们点击如图 4.10 指出的 `Upload` 按钮，IDE 即会自动开始编译程序、并下载至开发板。  
  
**<center>![图 4.10 Arduino IDE 中的 `Upload` 按钮](imgs/img_04_11.png)  
图 4.10 Arduino IDE 中的 `Upload` 按钮</center>**
  
若编译与下载成功完成，我们可在提示行内看到类似图 4.11 所示的下载成功的提示。  
  
**<center>![图 4.11 下载成功的提示](imgs/img_04_12.png)  
图 4.11 下载成功的提示</center>**
  
下载成功后，即可观察到开发板上的 LED 开始亮一秒、灭一秒的无限循环了，而且断电重新上电后程序依然还能执行。就与这几行简短的代码类似，我们只需要知道相关外设的操作函数就可以快速实现更多所需的功能，而无需特别关注这些函数的底层操作，可以体验到，Arduino 语言提高了嵌入式软件开发的便捷程度。这是因为，Arduino 语言将操作各个外设的底层代码封装成了一个个函数，组成了函数库。  
  
现在的芯片规模越来越大，功能越来越丰富，很多芯片厂商除了提供数据手册外也会提供一套函数库给开发者，因为库能够让开发变得更好、更快、更高效。不过，对于需要走向专业的学习者而言，只学习应用层面的开发是不够的，开发函数库也是需要学习的重要技能。那么，对于我们的 YADAN SoC 或 PULPino SoC，要如何从零开始写第一行代码呢，下一节将介绍如何使用 RISC-V GCC 工具链来更为底层地开发我们的程序。  

## 使用 RISC-V GCC 工具链开发底层程序  
在前边的[第 3.5 节](chap3.html#risc-v-gcc)介绍了 RISC-V GCC 工具链的安装方法。接下来我们将以控制 LED 闪烁为例来介绍使用 RISC-V GCC 工具链开发程序的流程。  
  



// TODO:  
  