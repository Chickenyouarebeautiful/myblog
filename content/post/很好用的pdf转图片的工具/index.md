---
title: "很好用的pdf转图片的工具"
description: 
date: 2025-09-12T22:48:40+08:00
image: 
math: 
license: 
hidden: false
comments: true
draft: false
tags: ['工具','小tips']
categories: ['tool']
---

# 最近下载了一个pdf但是只需要里面的图片

wps导出图片居然还收费,免费的话还有水印

永远不向黑恶势力妥协

找到一款很好用的pdf转图片的工具 免费开源  

*[github项目地址](https://github.com/oschwartz10612/poppler-windows/releases/)*

下载解压,把bin路径添加到环境变量

```cmd
# 把 PDF 转成 PNG
pdftoppm input.pdf output -png

# 把 PDF 转成 JPEG
pdftoppm input.pdf output -jpeg

# 转换指定页（例如第 2 页）
pdftoppm -f 2 -l 2 input.pdf output -png

# 设置分辨率（DPI，越大越清晰）
pdftoppm -r 300 input.pdf output -png
```


