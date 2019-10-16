---
title: 基于 Anime4K 的 Video2X 无损视频放大
date: 2019-10-7 17:28:15
tags:
  - Anime4K
  - Video2X
  - HIMEHINA
count: 1
os: 0
os_1: 10.0.17763.775 2019-LTSC
browser: 0
browser_1: 74.0.3729.169 Stable
place: 新家
key: 58
---
    《HIMEHINA 心灵的怒吼》直播源 720P 拉伸至 1080P 的尝试
<!-- more -->
## 0x00.前言
> https://pan.baidu.com/s/1gBimi2KfyP_oDvqh6V4IGA
![资源](https://i1.yuangezhizao.cn/Win-10/20191007173645.jpg!webp)
![审核过草](https://i1.yuangezhizao.cn/Win-10/20191007173737.jpg!webp)
![血赚](https://i1.yuangezhizao.cn/Win-10/20191007173222.jpg!webp)

然后`PanDownload 2.1.3`屯到本地发现竟然是`720P`，于是想着拉到`1080P`试试看……

## 0x01.[Video2X](https://github.com/k4yt3x/video2x)
> A lossless video enlarger/video upscaler achieved with waifu2x and Anime4K. https://k4yt3x.github.io/video2x/

![最新版 video2x-2.10.0-win32-light.zip 不提供完整包](https://i1.yuangezhizao.cn/Win-10/20191007174752.jpg!webp)
![video2x_setup.exe，网络不能](https://i1.yuangezhizao.cn/Win-10/20191007175701.jpg!webp)
![尝试源码安装，git 翻车现场](https://i1.yuangezhizao.cn/Win-10/20191007181523.jpg!webp)
![文件夹已炸](https://i1.yuangezhizao.cn/Win-10/20191007182100.jpg!webp)

## 0x02.[CUDA](https://developer.nvidia.com/cuda-toolkit-archive)
![于是去下了上一个提供完整包的 video2x-2.9.0-win32-full.zip](https://i1.yuangezhizao.cn/Win-10/20191007195541.jpg!webp)

发现选了`GPU`模式`CPU`仍然跑满，于是准备去安装`CUDA`+`cuDNN`即`NVIDIA`机器学习全家桶……
![这里仍然选择之前的 10.0，去看了下 TF 的文档支持仍然是这个版本（我怂，其实是懒得折腾了](https://i1.yuangezhizao.cn/Win-10/20191007200853.jpg!webp)

这里网络环境不好，于是选择了`cuda_10.0.130_win10_network.exe`在线安装……
![按需下载](https://i1.yuangezhizao.cn/Win-10/20191007203426.jpg!webp)
![卒](https://i1.yuangezhizao.cn/Win-10/20191007202921.jpg!webp)
![10，000 years later](https://i1.yuangezhizao.cn/Win-10/20191007203739.jpg!webp)
![今晚网络各种炸](https://i1.yuangezhizao.cn/Win-10/20191007204342.jpg!webp)
![再慢就要用中转机子了](https://i1.yuangezhizao.cn/Win-10/20191007204425.jpg!webp)
![安装依赖](https://i1.yuangezhizao.cn/Win-10/20191007204750.jpg!webp)
![后来发现只需运行该文件安装即可，然而需要良好的网络环境](https://i1.yuangezhizao.cn/Win-10/20191007205401.jpg!webp)
![于是变成了手动下载了……](https://i1.yuangezhizao.cn/Win-10/20191007205803.jpg!webp)
![顺便更新下版本](https://i1.yuangezhizao.cn/Win-10/20191007201335.jpg!webp)
![文件夹名实在是太难了……](https://i1.yuangezhizao.cn/Win-10/20191007213018.jpg!webp)

未完待续……