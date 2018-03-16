---
layout: post
title: 移动端测试与调试
categories: mobile
description: 移动端如何进行测试与调试
key: wzyugh2018-03-16
keywords: mobile, test, debugging, 移动端
---



## Charles代理
1. 下载最新版Charles，建议`v3.10.1`
2. 打开`Proxy->Proxy Settings` ，查看`port`。确定`Enable transparent HTTP proxying` 勾上。

## Charles抓包
 1. HTTP包就直接正常抓
 2. HTTPS
 1. 依次打开`Proxy->SSL Proxying Settings`
 2. 确保`Enable SSL Proxying Settings`已经勾选，在`Locations`栏输入要抓的域名，如`bm.nuomi.com`、`*`
 3. 打开手机连接上Charles的代理，选择`Allow`
 4. 依次打开`Help->SSL Proxying->Install Charles Root Certificate...`，手机访问提示的网址（一般情况是这个地址：http://charlesproxy.com/getssl，可以用二维码扫描访问），安装Charles SSL证书。
 

## Android设备调试

1. Android设备`USB线`连接PC。打开开发者模式
 2. 开启`USB调试模式`。
 3. 存储模式中`USB计算机连接`选择`媒体设备`，不要选择~~`相机、充电中`~~等。
 4. <font color="red">开发者选项中，`选择调试应用`选择要调试的app</font>。
 5. 勾选弹出的提示框。
6. Android设备访问PC服务器项目。
7. <font color="red">让Chrome可以翻墙</font>，第一次这样打开这个调试工具需要翻墙，后续就不用了。
8. 打开Chrome，新开Tab标签，输入`chrome://inspect`，如下图：
![图片](http://bos.nj.bpc.baidu.com/v1/agroup/dc4acc57fda015ac5456cb7562bb8071caa5bc8d)
图中从上到下的解释：

 - 手机品牌
 - 正在调试的app
 - 访问的文件地址
 - 调试按钮
 
9. 点击 `inspect`
10. 出现`Google Developer Tools`的调试页面，然后就可以打断点调试了：
![图片](http://bos.nj.bpc.baidu.com/v1/agroup/0c720d98e57a42a99dd9e9b3556781c361127b51)