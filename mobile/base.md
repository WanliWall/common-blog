# 基础概念

## 英寸
屏幕对角线长度
## 分辨率
+ 像素
  + 具有特定得位置和颜色
  + 图片或屏幕的最小组成单位
+ 屏幕分辨率
  + 屏幕具体由多少个像素点组成
  + 高分辨率不代表屏幕就清晰，还和尺寸有关
+ 图像分辨率
  + 图片的像素个数，比如800 x 400
  + 同一尺寸的同一张图片，分辨率越高，越清晰
+ PPI
  + Piexl Per Inch
  + 每英寸包含的像素个数
  + $\frac{\sqrt{水平像素点数^2+垂直像素点数^2}}{尺寸}$
+ DPI
  + Dot Per Inch
  + 每英寸包含的点数
  + 用DPI描述图片和屏幕，DPI应该和PPI等价，DPI最常用于描述打印机
  + 打印点的密度，打印机的DPI越高，打印效果就越好，同时也会消耗更多的墨点和时间
## 设备独立像素
用一种单位来告诉不同分辨率的手机，在页面上显示元素的大小是多少，这个单位就是设备独立像素，Device Independent Pixels，简称DIP或DP
+ 设备像素比
  + device pixel ratio，简称dpr，即物理像素和设备独立像素的比值
  + 如何获取
  + Web中，window.devicePiexlRatio
  + css中，可以使用媒体查询min-device-piexl-ratio
  + React Native中，可以使用PixelRatio.get()来获取
+ 移动端开发
  + 在IOS、Android和React Native开发，样式单位其实使用的都是设备独立像素
  + 写样式时需要把物理像素转换为设备独立像素
  + 最好的是，和设计沟通好，UI图按照设备独立像素来出
+ WEB端开发
  + 写CSS时，用到最多的单位就是px，即CSS像素，当页面缩放比例为100%时，一个CSS像素等于一个设备独立像素
  + CSS像素很容易被改变，当用户对浏览器进行放大，CSS像素会被放大，这时一个CSS像素就会跨域更多的物理像素
  + 页面的缩放系数 = CSS像素 / 设备独立像素
## 视口
+ 布局视口(layout viewport)
![layout viewport](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ce11243ea8b54da68c1b899a235c83d2~tplv-k3u1fbpfcp-watermark.awebp)
+ 视觉视口(visual viewport)
![visual viewport](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bacccff7697542f799ad99cd078de44c~tplv-k3u1fbpfcp-watermark.awebp)
+ 理想视口(ideal viewport)
![ideal viewport](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3c8562b88a6a4e6fb23c672b64cdcd40~tplv-k3u1fbpfcp-watermark.awebp)
+ Meta viewport
```html
<meta name="viewport" content="width=device-width; initial-scale=1; maximum-scale=1; minimum-scale=1; user-scalable=no;">

```
|key|值|描述|
|-|-|-|
|width|正整数或device-width|以pixels(像素)为单位定义布局视口的宽度|
|height|正整数或device-height|以pixels(像素)为单位定义布局视口的高度|
|initial-scale|0.0 - 10.0|定义页面初始缩放比例|
|minimun-scale|0.0 - 10.0|定义缩放的最小值，必须小于或等于maximum-scale的值|
|maximun-scale|0.0 - 10.0|定义缩放的最大值，必须大于或等于minimum-scale的值|
|user-scalable|yes或者no|如果为no，用户将不能放大或者缩小网页，默认为yes|

+ 移动端适配
  + 为了让页面获得更好的显示效果，必须让布局视口、视觉视口尽可能都等于理想视口
  + 设置initial-scale=1;就相当于让视觉视口等于理想视口
+ 缩放
  + 布局视口的宽度是width和视觉视口宽度的最大值
  + i若手机的理想视口宽度为400px，设置width=device-width，initial-scale=2，此时视觉视口宽度 = 理想视口宽度 / initial-scale即200px，布局视口取两者最大值即device-width 400px
  + 若设置width=device-width，initial-scale=0.5，此时视觉视口宽度 = 理想视口宽度 / initial-scale即800px，布局视口取两者最大值即800px
+ 获取浏览器窗口大小
  + window.innerHeight：获取浏览器视觉视口高度（包括垂直滚动条）。
  + window.outerHeight：获取浏览器窗口外部的高度。表示整个浏览器窗口的高度，包括侧边栏、窗口镶边和调正窗口大小的边框。
  + window.screen.Height：获取获屏幕取理想视口高度，这个数值是固定的，设备的分辨率/设备像素比
  + window.screen.availHeight：浏览器窗口可用的高度。
  document.documentElement.clientHeight：获取浏览器布局视口高度，包括内边距，但不包括垂直滚动条、边框和外边距。
  + document.documentElement.offsetHeight：包括内边距、滚动条、边框和外边距。
  + document.documentElement.scrollHeight：在不使用滚动条的情况下适合视口中的所有内容所需的最小宽度。测量方式与clientHeight相同：它包含元素的内边距，但不包括边框，外边距或垂直滚动条。




