---
title: Ubuntu 安装教程
cover: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/1628397182442.webp'
top_img: 'https://cdn.hatsusakuramiku.cn/hexo/img/gallery/post/1628397182442.webp'
tag:
  - 学习
category: 新萌指北
description: 自己总结的Ubuntu安装教程
swiper_index: 1
mathjax: true
comments: false
abbrlink: 3f19d5ec
date:
---

{% note warning flat %}
注意：该教程为本人是自己经验之谈，有一定迟滞性，仅作参考。
{% endnote %}

## 1. VMware虚拟机安装

### 1.1 安装VMware虚拟机软件

本教程使用的虚拟机软件为，VMware Workstation 16 Pro，可前往[官网](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)下载，下载安装后会有1个月试用期。

### 1.2 下载系统镜像

本教程使用的系统镜像为Ubuntu 20.04 LTS（可以适当使用Ubuntu 20 较高版本），请自行去[官网](https://cn.ubuntu.com/download/desktop)下载。

### 1.3 安装Ubuntu虚拟机

{% folding bule ,安装教程 %}

1. 打开安装好的VM，选择创建新的虚拟机
![步骤1](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/1.png "step 1")

2. 选择自定义（高级）并单击下一步
![步骤2](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/2.png "step 2")

3. 这个界面不需要更改，直接单击下一步
![步骤3](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/3.png "step 3")

4. 选择稍后安装操作系统，之后单击下一步
![步骤4](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/4.png "step 4")

5. 选择客户机操作系统为linux，版本选择你下载的Ubuntu 20.04 LTS镜像相对应的版本，我下载的是64位的，所以选择的是64位的
![步骤5](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/5.png "step 5")

6. 上面那一栏自定义你要安装的虚拟机的名称，下面那一栏是安装位置，默认位置为：C:\Users\你的电脑用户名称\Documents\Virtual Machines
![步骤6](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/6.png "step 6")

7. 这个界面设置设置在虚拟机内虚拟的处理器（CPU）的数量与单个处理器的核心数量，默认为2个CPU，单个CPU只有1核。我设置的是1个CPU，4个核心，具体可视自己情况而定。
![步骤7](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/7.png "step 7")

8. 设置分配给虚拟机的内存大小，依主机内存大小不同，其推荐内存大小不同，建议分配推荐内存大小
![步骤8](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/8.png "step 8")

9. 此页面设置为虚拟机添加的网络连接类型，如果不清楚的话，不用更改，直接点击下一步
![步骤9](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/9.png "step 9")

10. 设置I/O控制器类型，不用更改，直接使用推荐类型即可
![步骤10](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/10.png "step 10")

11. 设置为虚拟机创建的虚拟磁盘类型，亦可直接使用推荐类型
![步骤11](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/11.png "step 11")

12. 这个依自己而定，对小白，我推荐选择创建新的虚拟磁盘
![步骤12](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/12.png "step 12")

13. 为虚拟机分配存储空间，如果图简便可直接单击下一步
![步骤13](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/13.png "step 13")

14. 不用更改，直接单击下一步即可
![步骤14](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/14.png "step 14")

15. 在这个页面，单击自定义硬件
![步骤15](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/15.png "step 15")

16. 单击“新CD/DVD”选项
![步骤16](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/16.png "step 16")

17. 在连接一栏选择使用ISO映像文件，再单击浏览，选择你下载好的Ubuntu映像文件，再点击打开即可。（如果用不到设备中的打印机，推荐将其移除）之后点击关闭，就会回到第15步的页面。
![步骤17](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/17.png "step 17")

18. 点击完成，VM会自动创建客户机（或许会自动开启）
![步骤18](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/18.png "step 18")

19. 点击开启此虚拟机，VM会启动此虚拟机，之后会自动进入安装界面
![步骤19](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/19.png "step 19")

20. 之后出现这个界面，在这个界面请耐心等待加载
![步骤20](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/20.png "step 20")

21. 加载完成后出现如下界面，这是安装界面，选择系统语言，推荐选择英语，再点击Install ubuntu
![步骤21](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/21.png "step 21")

22. 选择键盘布局语言，推荐选择英语
![步骤22](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/22.png "step 22")

23. 推荐选择minimal installation，其他可以不用更改
![步骤23](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/23.png "step 23")

24. 可不用更改任何选项，直接点击install now，弹出的下一个界面亦不用管，直接下一步即可
![步骤24](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/24.png "step 24")

25. 选择你的地区，选择上海即可
![步骤25](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/25.png "step 25")

26. 设置你的账户名称，密码等，设置好后，点击下一步，自动安装，此过程耗时较长，请耐心等待
![步骤26](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/26.png "step 26")

27. 重启虚拟机即可安装完成
![步骤27](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/27.png "step 27")

28. 重启完成，输入密码登录后，弹出的一系列窗口都可以不用管，直接skip或next即可。之后会弹出software update窗口，请先更新，待更新完成后重启即可

{% endfolding %}

### 1.4 安装过程中可能出现的问题

1. Ubuntu安装过程中出现蓝屏，卡死等情况，而且重启电脑后再次安装依然出现这个问题：
我的电脑就出现过这种问题，可以试试开启Windows的wsl后再尝试安装，或许能解决（我的是使用这个方法解决了，其他的不清楚）。

2. 在选择键盘语言格式时，选择中文后发现下一步等选项不见了：
这个我也遇到过，不过咱也没有什么特别好的解决方法，只知道选择英语大概率不会出现这种情况，所以我推荐选择英语。

3. 安装Ubuntu时好慢呐，有什么办法能提高访问速度吗：
因为Ubuntu的官方服务器在国外，所以安装得很慢是十分正常的，可以试试在你的电脑上挂个梯子，开全局代理，或许速度会快很多。

4. 安装过程第28步提到了software update，可不可以不用更新：
进行software update是为了能顺利更改镜像源，需完成更新后方可进入更改镜像源的设置。

{% folding bule , wsl开启方法 %}

1. 点击任务栏的Windows图标，在搜索框中输入“启用”/“启用或关闭windows功能”，然后选择“启用或关闭windows功能”
![wsl1](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/wsl1.png " wsl 1")

2. 在弹出的窗口中翻找选项“适用于 Linux 的 Windows 子系统”
![wsl2](https://cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/wsl2.png " wsl 2 ")

3. 勾选“适用于 Linux 的 Windows 子系统”选项，点击确定后重启电脑即可
![wsl3](https//cdn.hatsusakuramiku.cn/hexo/img/post/zhenxun/wsl3.png " wsl 3 ")
