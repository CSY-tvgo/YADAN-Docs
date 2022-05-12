Welcome to YADAN's documentation!  
=========================================
欢迎访问鸭蛋的简介与快速入门指南！  
=========================================

.. image:: imgs/img_00_01.jpg

YADAN 项目包含 YADAN Core、YADAN SoC、YADAN Board，分别是 RISC-V 指令集的开源 CPU Core、开源 SoC、开源开发板，可帮助我们从嵌入式软件一直学习到数字系统和计算机架构。  

YADAN Board 是一块核心为 Anlogic FPGA 的可编程硬件设计学习平台，我们既能直接写硬件描述语言 (HDL) 在里边实现特定的数字系统、甚至是 CPU 与 SoC，又能部署 SoC 后将其视为常规 SoC 来写软件开发。利用这些特性和 YADAN 的配套资源，只需一块 YADAN Board，我们就可以学习电子与计算机工程学科中以下三个阶段的内容：  

+ **阶段一:** 部署已实现的 YADAN SoC，开始学习 **嵌入式软件**  
+ **阶段二:** 用裸 FPGA 开始学习使用硬件描述语言 **设计数字系统**  
+ **阶段三:** 参照 YADAN Core 与 SoC，开始学习设计 **RISC-V CPU Core 与 SoC**  

配套文档 **在未来将** 全部发布在 `YADAN 主文档：docs.yadanboard.com <http://docs.yadanboard.com/>`_，欢迎阅读。  

不过，截至目前（2022 年 5 月），因 YADAN 项目仍在推进中：  
+ `主文档 <http://docs.yadanboard.com/>`_ 中暂时只包含 **YADAN Board、SoC、Core 的技术参数**、和 **阶段一的教程**  
+ 如需 **阶段二的教程**，请临时访问 `这个帖子 <https://verimake.com/d/144>`_ 阅读  
+ **阶段三的教程** 仍在编写，暂时只能在 `这里 <https://gitee.com/verimake/yadansoc>`_ 浏览代码  

🛒 在淘宝搜索 `VeriMake <https://shop219297002.taobao.com/>`_，或者直接点击 `这里 <https://item.taobao.com/item.htm?id=663934271655>`_ 可以购买开发板。  
  
如果您在使用 YADAN Board 的过程中遇到问题、或者想分享你的成果，欢迎在 `VeriMake 论坛的 YADAN 标签下 <https://verimake.com/t/YADAN>`_ 参与讨论。如果发现文档中存在问题，欢迎在 `这个贴子 <https://verimake.com/d/33/>`_ 下留言讨论。

当前版本的更新时间为：2022 年 5 月 12 日 UTC+8，版本更新日志可以看 `这里 <https://github.com/CSY-tvgo/YADAN-Docs/#%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97>`_。

.. toctree::
   :numbered:
   :maxdepth: 1
   :caption: 目录
   
   YADAN Board 开发板介绍 <chap1.md>
   已适配的 SoC 的介绍 (YADAN SoC / PULPino SoC)<chap2.md>
   搭建开发环境 <chap3.md>
   使用 YADAN <chap4.md>
   几个入门实验 <chap5.md>

   附录：超级快速入门步骤 <chap6.md>
   附录：一些可能会遇到的问题（FAQ） <chap7.md>
   附录：下载相关附件 <chap8.md>
  

YADAN 在 RISC-V 中国峰会 2021 上的介绍
--------------------------------------------------

.. raw:: html

   <iframe src="https://player.bilibili.com/player.html?aid=546778671&bvid=BV19q4y1W7Jh&cid=373193875&page=1" allowfullscreen="true" width="100%" height="500" scrolling="no" frameborder="0" sandbox="allow-top-navigation allow-same-origin allow-forms allow-scripts"></iframe>

点击 `此处 <https://www.bilibili.com/video/BV19q4y1W7Jh>`_ 在哔哩哔哩上看完整视频，点击 `此处 <https://space.bilibili.com/356383684>`_ 在哔哩哔哩上关注 VeriMake。  
