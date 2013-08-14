# 响应式设计之媒体查询

```css
/* @media Rule */
@media all and (max-width: 1024px) {}

/*上面这条规则定义所有媒体类型（all），浏览器视窗的宽大于或等于1024px时适用的样式表（表达式: max-width: 1024px;）*/
```

```html
还可以在html的Link元素上指定media属性设置媒体查询
<link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
```

## 媒体类型

常见的媒体类型有所有(all)，屏幕（screen），打印（print），电视（tv）和盲文（braille）。

一个没有特别声明媒体类型的媒体查询，默认媒体类型是屏幕（screen）。

媒体查询表达式可能包含不同的媒体属性和属性值，然后分配是真还是假。当一个媒体属性和值都为真时，应用样式，否则忽略样式。

```css
/* 针对打印的样式表 */
@media print{}
```


## 逻辑运算符

媒体查询中的逻辑运算符，帮助建立强大的表达式。

在媒体查询中有三个不同的逻辑运算符，分别是与(and)，非（not）和唯一（only）。

1. and
```css
/* 在媒体查询中使用与逻辑运算符，容许添加额外的条件，以确保浏览器或是设备同时满足a，b，c条件等等。
多个媒体查询可以用逗号分开，作为一个筛选条件。
下面的例子就是选择满足宽度在800到1024之间的所有设备。 */
@media all and (min-width: 800px) and (max-width: 1024px) {}	
```

2. not
```css
/* 在查询中的非逻辑运算符，表示除了满足查询条件设备的所有设备都适用。
在这个例子表达式，就是应用于任何设备除了彩屏的，黑白屏或是单色屏幕都适用。
(and的优先级更高，所以这里标示的是“非 屏幕且彩屏”)*/
@media not screen and (color) {}	
```

3. only
```css
/* 下面表达式只匹配屏幕方向(orientation)是竖屏(portrait)，能够渲染的媒体查询的用户代理。*/
@media only screen and (orientation: portrait) {}	
```

## 媒体特性

### 媒体特性中的宽高

最常见的一种媒体特性围绕设备或浏览器视窗的宽高。

这些尺寸可以使用媒体特性中的height，width，device-height和 device-width获取到，并且这些特性均可以用min或max作为前缀，建立例如min-width 或 max-device-width的特性。

### 使用最大最小前缀 min,max

最大最小前缀在媒体特性中有相当多的地方使用。最小前缀表示一个值大于或是等于，而最大前缀表示一个值小于或是等于。
```css
/* 表达式匹配屏幕宽度大于320小于780的所有设备 */
@media all and (min-width: 320px) and (max-width: 780px) {}	
```

### 屏幕方向媒体特性 orientation

屏幕方向媒体特性决定一个设备是处于横屏还是竖屏。横屏模式显示宽大于高，而竖屏模式触发高大于宽。

这个媒体特性在移动设备上发挥很大的作用。
```css
/* 竖屏：landscape；横屏：portrait */
@media all and (orientation: landscape) {}	
```

### 像素比特性

特性包含设备像素比也有min和max前缀。具体来说，像素比功能非常时候高清设备，包括视网膜屏幕。这样的媒体查询要如下这样写。
```css
@media only screen and (-webkit-min-device-pixel-ratio: 1.3), only screen and (min-device-pixel-ratio: 1.3) {}
```

### 分辨率媒体特性

这个媒体特性是指在输出设备上的像素密度，也就是常说的每英寸的像素点数或是DPI。这个媒体特性也接受min和max前缀。此外，这个媒体特性可以表示，每像素多少点数(如1.3 dppx，表示每像素1.3个像素点),每厘米多少点数(如118 dpcm表示每厘米118个像素点),和其他长度单位的分辨率。
```css
@media print and (min-resolution: 300dpi) {}	
```

## 媒体查询浏览器支持

不幸的是，媒体查询在ie8及其以下的浏览器不能支持。

不过，幸好有一些插件对它们进行处理兼容。

1. [Respond.js](https://github.com/scottjehl/Respond/)是一个轻量级的插件，只是查找媒体查询中的min/max-width，在那些只使用媒体查询中完美的适用。
2. [CSS3-MediaQueries.js](https://code.google.com/p/css3-mediaqueries-js/)是一个更复杂，功能更强大的插件，支持更复杂的媒体查询。

不过，记住一点，就是任何插件都会有性能问题，也就是放缓网站的访问速度。所以在使用插件前要确保这个性能的损失是值得的。































