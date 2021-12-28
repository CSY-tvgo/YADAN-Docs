# 附录：一些可能会遇到的问题（FAQ）  
  
## 安装驱动程序后，开发板被识别为是来自 `dji-innovations inc.` 的设备  
  
测试人员在一台曾经连接过大疆的遥控器的电脑中发现，安装开发板的驱动程序后，开发板被识别为如图 7.1 所示的来自 `dji-innovations inc.` 的设备，且无法正常烧录程序。  
  
**<center>![图 7.1 开发板被识别为是来自 dji-innovations inc. 的设备](imgs/img_07_01.png)  
图 7.1 开发板被识别为是来自 `dji-innovations inc.` 的设备</center>**
  
原因可能是大疆的遥控器的驱动程序与开发板的驱动程序存在冲突。如果暂时不需要在电脑上使用大疆的遥控器，可以直接在 Windows 的 `设置 -> 应用与功能` 中搜索 `dji` 将它的驱动程序卸载干净。然后，再重新安装开发板的驱动程序，即可正常使用开发板。  
  
  
## 在 Boards Manager 中安装 YADAN 错误  
  
如果在 Arduino IDE 的 Boards Manager 中安装 YADAN 时提示 CRC 校验错误，可能是下载过程不太稳定导致，有以下两种方法可以重新安装，可任选其一。  
  
### 第一种方法：换用 GitHub 源下载  
如果你知道如何更加流畅地访问 GitHub，仅需打开 `File -> Preferences`，把之前在 `Additional Boards Manager URLs` 中填入的托管在 Gitee 的源的地址换为托管在 GitHub 上的源的地址：  
```
https://raw.githubusercontent.com/Edwin-zzp/YadanArduino/main/package_verimake_core_index.json
```
再尝试重新安装即可。
  
### 第二种方法：离线安装  
打开这个百度网盘页面
```
https://pan.baidu.com/s/1uzZ-Ic4XPclwRXgk5f-Z_g  提取码：3005
```
在里边找到 `离线安装开发板开发包.rar`，下载它并解压，可以得到 `YADAN` 文件夹，把这个文件夹复制到 `C:\Users\你的用户名\AppData\Local\Arduino15\packages` 文件夹下，重新打开 Arduino IDE，即可直接在开发板列表中找到 YADAN Board。  
  
使用这个方法要注意：  
+ `AppData` 是个隐藏文件夹，我们可以直接在 Windows 资源管理器的地址栏里输入路径来访问它，也可以在 Windows 的 `文件夹选项` 中勾选 `显示隐藏的文件夹` 然后在图形界面里找到它。  
+ 如果 `packages` 文件夹里边已经有了 `YADAN` 文件夹，可将其删除，再把新下载的文件夹复制进去。  
  
  
## 如果遇到其它问题  
  
欢迎访问 [VeriMake 论坛](https://www.verimake.com/)，在上边可以讨论你遇到的更多问题。  
  