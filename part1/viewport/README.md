# 视窗

如今用移动设备显示网站是一个很cool的事情。但是有时移动设备上的网站的显示辅助帮助有点不到位，特别是视窗的尺寸规模，对网站的处理。为了解决这些问题，苹果发明了视窗meta标签。

__写法：__
```html
<meta name="viewport" content="width=320, initial-scale=2.3, user-scalable=no">
```

使用content属性可以设置多个视窗规则，遵循这些规则：

1. 一个赋值语句作为一条规则：with=320。
2. 如有多条规则，使用逗号分隔的赋值语句："width = 320, initial-scale = 2.3"
3. 当赋值为数字时，仅数字部分会被保留：1x=>1,1024*9=>1024

## 视窗高宽 width | height

### 视窗宽 width

属性width设置移动设备显示网站的宽度。

__可用值：__
* 默认值是980。范围是从200到10,000。
* 可以设置关键字device-width，表示与设备同宽。

一个看上去很棒的网站的最好的处理方式，建议你使用设备宽度作为设备默认值。

```html
<meta name="viewport" content="width=device-width">
```

### 视窗高 height

属性height设置移动设备显示网站的高度。

__可用值：__
* 默认值根据属性width与设备的长宽比得出。范围是从223到10,000。
* 可以设置关键字device-height，表示与设备同高。

## 视窗比例

如何控制一个网站在手机设备上的显示比例，可以通过minimum-scale, maximum-scale, initial-scale,和 user-scalable 四个属性来控制。

### 初始比例 initial-scale 

在移动设备，页面是可以随意缩放的。可以使用initial-scale来定义第一次进入网站时的页面显示比例。

__可用值：__
* 数字，介于minimum-scale, maximum-scale之间，如果这两个属性没有设置，则是1到10。

一个看上去很棒的网站的最好的处理方式，建议你初始比例应该设置为1。

```html
<meta name="viewport" content="initial-scale=1">  
```

### 最大最小范围 minimum-scale, maximum-scale

最大最小范围值是确定视窗可以缩放到多大或是多小。

__可用值：__
* minimum-scale默认值是0.25，maximum-scale默认值是5。
* 最小范围值应是一个小于等于初始比例的值，最大范围值应是一个大于等于初始比例的值。但这两个值都应该是在0到10之间。

如果最大最小范围值设置为相同的初始值，将禁用缩放。关闭一个网站的缩放功能是一个坏主意。他不利于残疾人按照他们的意愿浏览一个网站。

```html
<meta name="viewport" content="minimum-scale=0">	
```

### 用户扩展 user-scalable 

确定用户是否可以放大和缩小—用户是否可以改变视口尺度。<br>
设置是yes允许缩放。默认是。

```html
<meta name="viewport" content="user-scalable=yes">	
```

## 视窗分辨率 target-densitydpi

一个屏幕像素密度是由屏幕分辨率决定的，通常定义为每英寸点的数量（dpi）。

这个目标分辨率接受如下值，他们是device-dpi, high-dpi, medium-dpi, low-dpi,或是一个实际的 DPI大小。

目标分辨率（target-densitydpi）值很少使用，但是在需要控制像素尤其有用。

```html
<meta name="viewport" content="target-densitydpi=device-dpi">	
```

__[Webkit不支持target-densitydpi](https://lists.webkit.org/pipermail/webkit-dev/2012-June/020914.html)__

## 组合视窗值

一个推荐的视窗值设置描述如下，同时使用设备宽度和初始比例属性。

```html
<meta name="viewport" content="width=device-width, initial-scale=1">	
```


## 参考资料

* [Safari Supported Meta Tags](http://developer.apple.com/library/safari/#documentation/appleapplications/reference/SafariHTMLRef/Articles/MetaTags.html)
