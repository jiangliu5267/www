---
title: EVB_MX_Plus 对接腾讯云物联网开发平台
date: 2020-1-19 19:27:36
tags:
  - TencentOS-tiny
  - EVB_MX_Plus
  - STM32L4
count: 1
os: 0
os_1: 10.0.17763.973 2019-LTSC
browser: 0
browser_1: 74.0.3729.169 Stable
place: 新家
key: 70
---
    烧错例程 == 浪费周六
    I GOOD VEGETABLE A
<!-- more -->
## 0x00.前言
> 话不多说，直接上图

![嗯？](https://i1.yuangezhizao.cn/Redmi-K20Pro/IMG_20200119_193052.jpg!webp)
![嗯？？](https://i1.yuangezhizao.cn/Redmi-K20Pro/IMG_20200119_193134.jpg!webp)

上午社畜（没错周日）接近十二点的时候才看到的，去`gh`一看猛然发现竟然有两个`_sdk_data_template`，不禁一身冷汗`(╯°Д°)╯︵┻━┻`
晚上回家才发现非常不巧地选错了，草`ヽ(｀Д´)ﾉ︵ ┻━┻ ┻━┻ `

![更改联网信息](https://i1.yuangezhizao.cn/Win-10/20200119194217.png!webp)
![更改平台信息](https://i1.yuangezhizao.cn/Win-10/20200119194442.png!webp)

## 0x01.调试
看了眼原理图发现了意外的收获，这个`智能路灯`的拓展板上不仅有灯还有`温、湿、亮`度传感器，太强了`(￣へ￣)`
![惊了](https://i1.yuangezhizao.cn/Win-10/20200119195721.jpg!webp)
![这么小！](https://i1.yuangezhizao.cn/Redmi-K20Pro/IMG_20200119_195907.jpg!webp)

## 0x02.运行
![点了个灯](https://i1.yuangezhizao.cn/Win-10/20200119212212.png!webp)
![关了个灯](https://i1.yuangezhizao.cn/Win-10/20200119212224.png!webp)

未完待续……