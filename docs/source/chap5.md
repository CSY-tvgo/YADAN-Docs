# 几个入门实验  
  
## 实验一、使用 Arduino IDE 在 YADAN Board 上开发程序  
  
### 实验目的  
1. 了解和熟悉使用 Arduino IDE 给 YADAN Board 开发程序的方法  
  
2. 熟悉和掌握 YADAN Board 的 UART 串口和 GPIO 的使用方法  

### 实验内容
1. 了解和学习 Arduino 语言中使用 UART 串口的相关函数，尝试编写代码通过 UART 串口发送 `hello,world`，尝试编写代码接收 PC 通过 UART 串口调试助手发送来的数据。了解和学习 UART 串口收发的数据格式，了解 ASCII 和 HEX 在 UART 串口收发中的区别。  
  
2. 了解和学习 Arduino 语言中使用 GPIO 和 PWM 的相关函数，尝试编写代码使用 PWM 控制 LED 的亮暗程度，尝试通过 PWM 调光来实现呼吸灯的效果。  
  
3. 尝试将上述的 1、2 结合，编写代码，使得 YADAN Board 能通过 UART 串口接收 PC 发送来的参数以调整呼吸灯的效果，例如调整呼吸频率、总体亮度等等，同时开发板可以反馈当前呼吸灯参数给 PC。  
  
### 实验解答  
使用 Arduino 的库可以很快地完成以上开发任务，下面是要使用的相关库函数。  
1. GPIO 相关函数  
   ```
   pinMode(pin, mode);           // 设置引脚模式  
   digitalWrite(pin, value);     // 设置引脚的输出值  
   analogWrite(pin, value);      // 设置引脚输出 PWM 波  
   delay(ms);                    // 毫秒延时函数  
   ```
   详情请参考 Arduino Reference:  
   [https://www.arduino.cc/reference/en/](https://www.arduino.cc/reference/en/)  
  
2. UART 串口的相关函数  
   详情请参考 Arduino Reference:  
   [https://www.Arduino.cc/reference/en/language/functions/communication/serial/](https://www.Arduino.cc/reference/en/language/functions/communication/serial/)  

## 实验二、 RISC-V GCC 工具链的熟悉与使用
### 实验目的  
1. 学习和掌握第四章中 RISC-V GCC 工具链的使用方法  
  
2. 了解和熟悉下载程序的使用  
  
### 实验内容  
1. 在百度网盘上下载样例空工程，使用 VS Code 打开目录 `Demoproject`，在里面 `main.c` 文件中编写图 4.12 中让灯闪烁的代码。使用 `wincompile.py` 编译工程，获得 `simple.bin` 文件。  
  
2. 尝试使用下载程序 `YADANdownload.py`，参照第四章里方法将 `.bin` 文件下载到开发板上观察 LED 的闪烁现象。  
  
3. 修改、优化代码。例如尝试自己配置定时器而非直接使用 `delay()` 来实现延时。  
  
### 实验解答  
#### 有关寄存器级操作  
在第四章样例程序的图 4.12 中，使用了  
```
PADDIR = 1 << 13;
```
这样的语句来设置 13 号引脚为输出模式，其实是不合理的。因为这样的语句会同时将 13 号引脚之外的其它所有引脚设置为输入模式，也就是影响了其它引脚原来的状态。  
  
所以，在进行寄存器级的操作时，如果只想操作某一个位，需要使用位操作。比如想仅设置 13 号引脚为输入模式、而不想改变其它引脚的状态时，可以使用类似这样的语句  
```
PADDIR |= 1 << 13;
```
这样的语句会仅将 `PADDIR` 寄存器的第 13 位置为 1，而不改变其它位原来的值。  
  
#### 有关定时器  
样例工程中已预先声明了定时器中断相关的函数，我们若需要使用定时器，仅需重写相应的函数即可，一共有 4 个，如下：
```
void ISR_TA_OVF (void);  // Timer_A 的溢出中断
void ISR_TA_CMP (void);  // Timer_A 的比较中断
void ISR_TB_OVF (void);  // Timer_B 的溢出中断
void ISR_TB_CMP (void);  // Timer_B 的比较中断
``` 
除此之外，我们还需设置定时器的 CTRL 寄存器 (Timer Control)。如果需要使用比较中断，还需设置 CMP 寄存器 (Timer Compare)，当定时器计数值达到 CMP 中设定值时，会触发中断函数 `ISR_T?_CMP()`。  
(寄存器的详细介绍请参考第二章)
  

## 实验三、函数库设计
### 实验目的
1. 学习和熟悉 YADAN Core 或 Zero-riscy 的相关外设库编写的方法  
  
2. 了解和学习 I²C 协议  
  
### 实验内容
1. 学习编写 GPIO 库函数  
  
2. 设计并编写 UART 串口常用的库函数  
  
3. 学习 I²C 协议，编写 I²C 库函数  
  
### 实验解答
#### 编写 GPIO 的库函数  
在实验二中，我们通过寄存器级的操作已经实现了 GPIO 的使用，但是直接操作寄存器的代码的可读性不是很好，于是我们可以设计并编写库函数来更方便地操作 GPIO。  
  
在设计库函数时，要先考虑操作 GPIO 可能需要哪些功能，例如设置 GPIO 输入输出模式、控制输出值、读取输入值等，然后再编写具体的函数实现。在编写时，还需要使函数具有一定的通用性，例如，设置 GPIO 输入输出模式的函数可以编写如下：
   ```
   void set_gpio_pin_direction(int pinnumber, int direction)
   {
       volatile int old_dir;
       old_dir = *(volatile int*) (GPIO_REG_PADDIR);
       if (direction == 0)
           old_dir &= ~(1 << pinnumber);
       else
           old_dir |= 1 << pinnumber;
       *(volatile int*) (GPIO_REG_PADDIR) = old_dir;
   }
   ```
#### 编写 UART 串口的库函数  
仿照 GPIO 的库的编写方式，我们可以继续尝试编写 UART 串口的库函数，例如可以尝试实现以下函数：  
```
void uart_set_cfg(uint16_t baud);                  // UART 设置波特率函数
void uart_sendchar(unsigned char c);               // UART 发送字符函数
void uart_send(const char* str, unsigned int len); // UART 发送字符串函数
char uart_getchar();                               // UART 接收一个字符函数
void uart_wait_tx_done(void);                      // UART 查询传输是否结束的函数
```

#### 编写 I²C 的库函数  
也可以继续尝试编写 I²C 通信接口的库函数，例如可以尝试实现以下函数：  
```
void I2C_setup(int prescaler, int enable);  // I²C 初始化函数，可设置分频系数，启用I²C
void I2C_send_data(int value);              // I²C 发送数据函数
void I2C_send_command(int value);           // I²C 发送命令、设置 I²C 动作的函数：
int I2C_get_status(void);                   // I²C 状态获取函数
int I2C_get_data(void);                     // I²C 读数据函数
int I2C_get_ack(void);                      // I²C 应答信号获取函数
int I2C_busy(void);                         // I²C 忙信号查询函数
```

## 实验四、综合实验
### 实验目的  
  1. 学习更多外设的原理，并编写函数库  
  
  2. 将不同外设综合起来，学习系统设计  
  
### 实验内容  
  不限制设计内容，推荐设计一个小系统以实现某种应用功能  
  
### 参考设计  
  1. 温湿度显示系统  
  使用 DHT11 温湿度传感器采集温湿度信息，通过 UART 串口发送到 PC 机显示。  
  DHT11 是一款单总线通信的温湿度传感器，仅需一个上拉的 GPIO 端口就可以实现数据传输。完成此设计需要了解 DHT11 的通信方式，并编写相应的库函数，实现对 DHT11 的驱动。  
  
  2. 编写一个 GUI 库实现绘图功能  
  实验三编写了 I²C 库，我们可以借助它驱动 I²C 接口的 128x64 的 OLED 点阵显示屏。  
  在本设计中，我们可以尝试编写一个 GUI 库，实现画点、画线、画常见图形、画字符等操作。  
  