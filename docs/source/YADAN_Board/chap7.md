# 附录：一些可能会遇到的问题  
  
## 安装驱动程序后，开发板被识别为是来自 `dji-innovations inc.` 的设备  

测试人员在一台曾经连接过大疆的遥控器的电脑中发现，安装开发板的驱动程序后，开发板被识别为如图 7.1 所示的来自 `dji-innovations inc.` 的设备，且无法正常烧录程序。  
  
**<center>![图 7.1 开发板被识别为是来自 dji-innovations inc. 的设备](imgs/img_07_01.png)  
图 7.1 开发板被识别为是来自 `dji-innovations inc.` 的设备</center>**
  
原因可能是大疆的遥控器的驱动程序与开发板的驱动程序存在冲突。如果暂时不需要在电脑上使用大疆的遥控器，可以直接在 Windows 的 `设置 -> 应用与功能` 中搜索 `dji` 将它的驱动程序卸载干净。然后，再重新安装开发板的驱动程序，即可正常使用开发板。  
  
  
## 在 Boards Manager 中安装 YADAN 错误  

如果在 Arduino IDE 的 Boards Manager 中安装 YADAN 时提示 CRC 校验错误，可打开 `File -> Preferences`，把之前在 `Additional Boards Manager URLs` 中填入的托管在 Gitee 的源的地址换为托管在 GitHub 上的源的地址：  
```
https://raw.githubusercontent.com/Edwin-zzp/YadanArduino/main/package_verimake_core_index.json
```  
再尝试重新安装。
  
  
## 如果遇到其它问题  
  
欢迎访问 [VeriMake 论坛](https://www.verimake.com/)，在上边可以讨论你遇到的更多问题。  
  