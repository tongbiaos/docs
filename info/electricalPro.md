---
typora-root-url: ./
typora-copy-images-to: ..\image\electricalPro
---

# 电子设备

## 专业英语

digital scope 数字示波器

## 仪器仪表

### can分析仪

#### 波特率侦测

![1672](/../image/electricalPro/1672.png)

### 示波器

#### 总结归纳

##### 探头

所有探头的x1档都只有几M，测量高频的时候会衰减得很厉害，所以测量高频时一定要使用x10档位。

#### 乐拓虚拟示波器

##### 说明

在淘宝上花了一千多大洋买了一个虚拟示波器，在网上看一些评论都说虚拟示波器不是太好，这里我自己体验一下。

![image-20210514202416690](/../image/circuit/image-20210514202416690.png)

主要参数：带宽100MHz、采样率1G、硬件触发、扩展13MHz信号发生器

![image-20210514202806131](/../image/circuit/image-20210514202806131.png)

![image-20210514211327666](/../image/circuit/image-20210514211327666.png)

收到的实物如下：

![image-20210514202711838](/../image/circuit/image-20210514202711838.png)

主要资料位置及软件：

![image-20210514204146900](/../image/circuit/image-20210514204146900.png)

在B站上还有很多视频教程，具体可参考上面提到的文档《LOTO仪器视频演示和应用文档合集20201109.pdf》

![image-20210514212957454](/../image/circuit/image-20210514212957454.png)

##### 探头

虚拟示波器设备本身的电压输入范围为±5v，设备标配的为1X/10X 的**40M** 探头两根: 当选择 1X 档 位时,电压输入范围为±5v,当选择 10X 档位时,电压输入范围为±50v; 如果使用选购的 100X 探头,电压输入范围为±500v。

选购隔离差分模块可以测量±800v。 

【我看视频上说探头的带宽为60M，但是在文档《LOTO虚拟示波器OSCH02系列数据手册V19》的探头介绍中又写探头为40M，最终看实际收到的探头标识为100M】

![image-20210515084111031](/../image/electricalPro/image-20210515084111031.png)

###### **1.衰减开关**

由于设备本身的量程是±5v,所以此时只能测量±5v 范围内的电压信号。 而当衰减开关被拨动到10X位置时,探头尖端所接触的被测电压信号将被衰减到十分之一后送入设备,所以此 时可以测量±50v 以内的电压信号。

![image-20210514211853130](/../image/circuit/image-20210514211853130.png)

10X档位拥有更好的频率特性和更宽的带宽,所以当遇到带宽和频率瓶颈时,可以尝试使用10X档位获得更好的测量效果。

![image-20210514212119578](/../image/circuit/image-20210514212119578.png)

###### **2.补偿电容**

![image-20210514212241007](/../image/circuit/image-20210514212241007.png)

使用 10X 档位时,可以通过调节探头上的补偿电容对探头的频率特性进行修正。将探头衰减开关拨至10X档位,并连接设备自带的标准方波参考信号,调节补偿电容可以将过补偿或者欠补偿的探头校正到合适状态。 

X1 档位无法进行探头校正。

![image-20210514212258502](/../image/circuit/image-20210514212258502.png)

【我还是第一次知道还有补偿电容呢】

###### 3.探头校正

PWM设置方法

![image-20210516112718359](/../image/electricalPro/image-20210516112718359.png)

###### **4.探头接地夹**

探头接地夹与虚拟示波器电路的地直接相连,并且通过 USB 线缆与 PC 地相连。在使用电源插座供电的 PC 时,PC 地通过三芯电源插孔中的保护地孔与大地相连。

![image-20210514212514708](/../image/circuit/image-20210514212514708.png) 

所以使用时,请确保探头的接地夹所接的被测电路地电位与 PC 使用的地等电位，否则会导致漏电, 短路或测量错误, 严重时会导致设备损坏

##### 60v过压保护实测

视频网址：https://www.bilibili.com/video/BV1o5411t7Mc

在这个视频中，实测了示波器探头在x1档时，测量了60V的电压，示波器仍然不会被损坏。但因为设备本身的电压输入范围为±5v，所以在探头x1档位时，只能测到±5v的电压，而并不能正确测量到60V的电压。

示波器探头x1档，测量范围为±5v，保护范围为±60v

示波器探头x10档，测量范围为±50v，保护范围为±600v

![image-20210514211644026](/../image/circuit/image-20210514211644026.png)

##### 对比台式示波器

视频网址：https://www.bilibili.com/video/BV1nK411j7tj

视频中，使用虚拟示波器OSC802和台式示波器来同时测量25M的信号发生器

虚拟示波器OSC802参数：采样率为？？，带宽为25M

台式示波器参数：采样率为2G Sa/s，带宽为200M

探头的标称带宽为6M（x1），60M（x10）

![image-20210514214753037](/../image/circuit/image-20210514214753037.png)



###### 空载0噪声比较

探头x1

空载时，同样设置电压档位为1V每格（1V/DIV），模拟示波器的0输入噪声为109mv，台式数字示波器的电压范围为120~180mv。

![image-20210514215721892](/../image/circuit/image-20210514215721892.png)

【我实测了一下自己0输入噪声为70mv，我的型号是OSCH02MS】

![image-20210515090108376](/../image/electricalPro/image-20210515090108376.png)

###### 1MHz正弦波比较

使用两个示波器同时测量了1MHz，峰峰值为4V的正弦波。

探头x1

OSC802：电压3.94V

DS：电压4.08~4.12V

![image-20210515090758450](/../image/electricalPro/image-20210515090758450.png)

###### 20MHz正弦波比较

使用两个示波器同时测量了20MHz，峰峰值为4V的正弦波。

探头x1

OSC802：电压2.19V

DS：电压1.40V

![image-20210515091147033](/../image/electricalPro/image-20210515091147033.png)

###### 25MHz正弦波比较

使用两个示波器同时测量了25MHz，峰峰值为4V的正弦波。

探头x1

OSC802：电压1.97V

DS：电压0.92V

![image-20210515091430445](/../image/electricalPro/image-20210515091430445.png)

探头x10

![image-20210515091809881](/../image/electricalPro/image-20210515091809881.png)

###### 结论

上述两款示波器在测试过程中，表现基本一致。

##### 1G采样率的优势

视频网址：https://www.bilibili.com/video/BV1ft4y1m7vj/?spm_id_from=333.788.videocard.3

型号：OSCH02

视频中提到OSCH02单通道时能做到1G的等效采样，250M的实时采样，带宽可以到100M。

单通道模式下，采样率可提高到250M

![](/../image/electricalPro/image-20210515095053372.png)

![image-20210515095118382](/../image/electricalPro/image-20210515095118382.png)

时间档位设置为10ns时，能有1G的等效采样

![image-20210515095148333](/../image/electricalPro/image-20210515095148333.png)

##### 方波、PWM、单次脉冲输出

参考视频：https://www.bilibili.com/video/BV1X5411h7Kt

参考视频：https://www.bilibili.com/video/BV16f4y1q7ce

仪器的DE1口的第6引脚可以输出标准方波、PWM和脉冲。

![image-20210516120653095](/../image/electricalPro/image-20210516120653095.png)

![image-20210516120842705](/../image/electricalPro/image-20210516120842705.png)

实际操作，打开软件右下角的“PWM|Pulse”按键，在弹窗中可设置方波、PWM和脉冲。

![image-20210519112913622](/../image/electricalPro/image-20210519112913622.png)

可以看到弹窗的左下角显示了脉冲宽度。

![image-20210519112556380](/../image/electricalPro/image-20210519112556380.png)

查看脉冲时，需要使用脉冲触发模式观测，这样比较容易看到发出来的脉冲。

注意：实际使用中，有时候按下Pulse没有反应，不知道是没有发出脉冲，还是没有捕获到，这个时候可尝试重新启动连接一下示波器。

![image-20210519115118160](/../image/electricalPro/image-20210519115118160.png)

##### 通讯协议解析

![can数据](/C:/Users/Administrator/Desktop/can数据.jpg)

##### 信号发生器

视频链接：https://www.bilibili.com/video/BV1jJ411r7a9

按视频中说，最大频率可以为13MHz。

一个旋钮是 增益按钮，一个旋钮是 偏置电压。

![image-20210518190118212](/../image/electricalPro/image-20210518190118212.png)

![image-20210518174113856](/../image/electricalPro/image-20210518174113856.png)

支持扫频功能

![image-20210524161823175](/../image/electricalPro/image-20210524161823175.png)



## 电池

### 锂电池

手机锂电池设定的温度限制一般在40-60度

#### 磷酸铁锂

#### 三元锂

#### 聚合物

## 简单评测

### 机甲大师

官网：https://www.dji.com/cn/robomaster-s1

#### 1.主要部件介绍

![image-20210513134255734](/../image/circuit/image-20210513134255734.png)

![image-20210513134321451](/../image/circuit/image-20210513134321451.png)

![image-20210513134337382](/../image/circuit/image-20210513134337382.png)

![image-20210513134344855](/../image/circuit/image-20210513134344855.png)

![image-20210513134351833](/../image/circuit/image-20210513134351833.png)

![image-20210513134358241](/../image/circuit/image-20210513134358241.png)

#### 2.接线顺序

电源线

![img](/../image/circuit/wps1.jpg) 

击打模块

![img](/../image/circuit/wps2.jpg) 

![img](/../image/circuit/wps3.jpg) 

击打模块线

![img](/../image/circuit/wps4.jpg) 

电机线

![img](/../image/circuit/wps5.jpg) 

云台线

![img](/../image/circuit/wps6.jpg) ![img](/../image/circuit/wps7.jpg)

![img](/../image/circuit/wps8.jpg) 

扬声器

![image-20210513134639677](/../image/circuit/image-20210513134639677.png)

水弹发射器线

![img](/../image/circuit/wps11.jpg) 

智能中控线

![img](/../image/circuit/wps12.jpg) 

摄像头

![img](/../image/circuit/wps13.jpg)

#### 3.体验总结

麦克纳姆轮的运动效果确实比较有意思，麦轮+云台摄像头 的运动控制逻辑是比较让我耳目一新的，其转弯方式逻辑是滑动屏幕进而控制云台摄像头的方向，当云台摄像头与车体底盘有方向差时，麦轮继而运动，修正到与云台摄像头方向一致。

常见的运动方式是控制器的左右，直接控制轮系运动，调整车体底盘向左转弯和右转弯。而机架大师的左右就是平移的左右，而非转弯。



