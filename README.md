# YADAN's Documentation  

中文版 (zh_CN): [![Documentation Status](https://readthedocs.org/projects/yadan/badge/?version=latest)](http://docs.yadanboard.com/zh_CN/latest/?badge=latest)  
Other Languages: Coming...  

## 介绍 Introduction  

[![](docs/source/imgs/img_00_01.jpg)](http://docs.yadanboard.com/)  

**快速链接:** [📖主文档](http://docs.yadanboard.com/) [🥂官方论坛](https://verimake.com/t/YADAN) [🛒购买开发板](https://item.taobao.com/item.htm?id=663934271655)  

YADAN 项目包含 YADAN Core、YADAN SoC、YADAN Board，分别是 RISC-V 指令集的开源 CPU Core、开源 SoC、开源开发板，可帮助我们从嵌入式软件一直学习到数字系统和计算机架构。  

YADAN Board 是一块核心为 Anlogic FPGA 的可编程硬件设计学习平台，我们既能直接写硬件描述语言 (HDL) 在里边实现特定的数字系统、甚至是 CPU 与 SoC，又能部署 SoC 后将其视为常规 SoC 来写软件开发。利用这些特性和 YADAN 的配套资源，只需一块 YADAN Board，我们就可以学习电子与计算机工程学科中以下三个阶段的内容：  

+ **阶段一:** 部署已实现的 YADAN SoC，开始学习 **嵌入式软件**  
+ **阶段二:** 用裸 FPGA 开始学习使用硬件描述语言 **设计数字系统**  
+ **阶段三:** 参照 YADAN Core 与 SoC，开始学习设计 **RISC-V CPU Core 与 SoC**  

配套文档 **在未来将** 全部发布在 [YADAN 主文档：docs.yadanboard.com](http://docs.yadanboard.com/)，欢迎阅读。  

不过，截至目前（2022 年 5 月），因 YADAN 项目仍在推进中：  
+ [主文档](http://docs.yadanboard.com/) 中暂时只包含 **YADAN Board、SoC、Core 的技术参数**、和 **阶段一的教程**  
+ 如需 **阶段二的教程**，请临时访问 [这个帖子](https://verimake.com/d/144) 阅读  
+ **阶段三的教程** 仍在编写，暂时只能在 [这里](https://gitee.com/verimake/yadansoc) 浏览代码  

🛒 在淘宝搜索 [VeriMake](https://shop219297002.taobao.com)，或者直接点击 [这里](https://item.taobao.com/item.htm?id=663934271655) 可以购买开发板。  

[docs.yadanboard.com](http://docs.yadanboard.com/) 主文档的网页由 Read the Docs 渲染与托管，源文稿托管在 GitHub 上的 [这个仓库](https://github.com/CSY-tvgo/YADAN-Docs) 里。如果您在使用 YADAN Board 的过程中遇到问题、或者想分享你的成果，欢迎在 [VeriMake 论坛的 YADAN 标签下](https://verimake.com/t/YADAN) 参与讨论。如果发现文档中存在问题，欢迎在 [这个贴子](https://verimake.com/d/33) 下留言讨论。  

点击 [此处](http://docs.yadanboard.com/) 可以阅读鸭蛋的中文主文档。  

### English Introduction  
YADAN Project includes YADAN Core, YADAN SoC, YADAN Board. They are open-sourced RISC-V CPU Core, SoC, development board. YADAN Board is a programmable platform based on Anlogic FPGA, and we can deploy an YADAN SoC integrated with an YADAN Core on it. YADAN is designed for education, it can help a starter learn from embedded programming to digital system and computer architecture using ONE development board.  
  
English version of this documentation would be released later, because we are still testing and improving YADAN and its documentation.  
  
YADAN Project was firstly introduced on RISC-V World Conference China 2021.  
  
PS: "YADAN" in Chinese is "鸭蛋 (Yā Dàn)", pronounced like /jɑː dæn/, which means duck's egg. We named it as "YADAN" because it was born in Nanjing, a Chinese city which has many duck cuisines with great reputation, and we expect each starter can enjoy benefit from YADAN and learn well in EECS-related discipline just like breaking the shell from an egg.  
  
## 版本更新日志 Update Logs  
  
| 日期                | 内容                                                                                                                                                       |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2021 年 8 月 23 日  | 创建了这个 Read the Docs 文档                                                                                                                              |
| 2021 年 9 月 3 日   | 把文档更改成了鸭蛋配色                                                                                                                                     |
| 2021 年 9 月 6 日   | 给文档配置了域名 [docs.yadanboard.com](http://docs.yadanboard.com)                                                                                         |
| 2021 年 10 月 8 日  | 发布好了第一个版本的所有内容                                                                                                                               |
| 2021 年 10 月 15 日 | 发布好了[《附录：超级快速入门步骤》](http://docs.yadanboard.com/zh_CN/latest/chap6.html)                                                                   |
| 2021 年 12 月 28 日 | 上传了 [开发板的原理图](http://docs.yadanboard.com/zh_CN/latest/chap1.html)；在 [FAQ](http://docs.yadanboard.com/zh_CN/latest/chap7.html) 里增加了一些内容 |
| 2022 年 1 月 7 日   | 增加了[《附录：下载相关附件》](http://docs.yadanboard.com/zh_CN/latest/chap8.html)                                                                         |
| 2022 年 5 月 10 日  | 发布了适配阶段二的教程[《在 YADAN Board 上入门 Verilog》（暂时先放在论坛中）](https://verimake.com/d/144)，并优化了相关介绍                                |

