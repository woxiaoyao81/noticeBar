<!--
 * @Descripttion: 
 * @version: 
 * @Author: woxiaoyao
 * @Date: 2020-10-15 16:18:26
 * @LastEditTime: 2020-10-15 19:45:33
-->
原文网址 <https://ext.dcloud.net.cn/plugin?id=2553>

## NoticeBar通告栏

支持水平、垂直两个方向的通告栏组件

### 更新记录

1.0.0（2020-08-18）
---------------------
支持水平、垂直两个方向的通告栏

### 一、使用说明
1. 解压下载的压缩包，将组件放在项目的components目录下

2. 引用组件

```vue
<wyb-noticeBar :text="['黑夜赐予我做梦的权利', '让我某一刻相信', '有不尽的晨曦', '会爬过脚下的土地']" />
```

3. Demo体验地址：<http://m.wybfiles.cn:82>（请用手机访问，或用桌面浏览器启动手机调试模式）

4. 如果觉得我的插件还不错，可以下载我的插件的示例集合Demo => [传送门](http://tomcat.wybfiles.cn/download/wyb-demo.zip)，里面有我全部的插件以及全部插件的示例工程

### 二、参数说明

1. Props  

    1-1. 整体参数

|参数名		|类型			|默认值		|说明			|可选值	|
|:--------:|:-------------:|:--------:|:------------:|:----:|
|type	|String		|"hori-connect"		|通告栏的滚动方向与动画类型		|hori-connect：水平衔接/hori-break：水平不衔接/vert：垂直滚动|
|width	|String\/Number		|屏宽		 |通告栏的宽度（单位：px，内部转化为rpx，无需担心自适应问题）|-		|
|height	|String\/Number		|70			|通告栏的高度（单位：rpx）									|-		|
|color	|HexColor		|"#f5a300"		|通告栏的整体颜色，不能使用rgb(r,g,b)						|-		|
|bgColor|HexColor\RgbColor	|color减淡85%	|通告栏的背景颜色										|-		|
|text	|Array	|-		|通告栏显示的文字，数组形式。hori-connect：数组中的所有元素一行显示。vert & hori-break：数组按元素一个一个显示	|-		|
|font-weight|String		|normal			|通告栏文字的粗细，同css									|100~900，normal，bold，bolder|
|font-size	|String/ Number		|27		|通告栏文字字体大小（单位：rpx）							|-		|
|has-border	|Boolean	|flase			|通告栏是否有边框								|true\|false|
|scroll		|Boolean	|true			|通告栏是否滚动									|true\|false	|
|show-icon	|Boolean	|true			|是否显示通知图标								|true\|false	|
|show-more	|Boolean	|true			|是否显示查看更多图标							|true\|false	|
|show-close	|Boolean	|false			|是否显示关闭图标								|true\|false	|
|url		|String		|-				|点击查看更多时要跳转的url，相对/绝对路径均可				|-		|
|extend-more-area	|Boolean	|flase	|点击文字部分是否同样触发查看更多事件			|true\|false	|

    1-2. hori-connect专用参数

|参数名											|类型	|默认值	|说明						|可选值	|
|:-:|:-:|:-:|:-:|:-:|
|join											|String	|4个空格|连接text数组元素的字符串	|-		|
|space-const|Number	|0							|每次重复出现的间隔常数 。=0 时代表前一次刚消失，下一次就出来；<0 时代表前一次还没消失，下一次就出来；>0时代表前一次结束后，过一会儿下一次才出来|-		|
|speed											|Number	|40		|文字滚动速度（单位：px/s）	|-		|
	
	1-3. vert & hori-break专用参数
    
|参数名		|类型	|默认值	|说明|可选值	|
|:-:|:-:|:-:|:-:|:-:|
|time		|Number	|3000	|每次切换后的停留时间（单位：ms）	|-		|
|duration	|Number	|1000	|每次切换时的动画时间（单位：ms）	|-		|

### 三、其他说明

1. 图标都关掉，可以当跑马灯用；
2. hori-connect是用@keyframes关键帧动画实现的。vert和hori-break是封装了uni-app官方的swiper组件实现的，swiper里面只有两个swiper-item，数组元素是动态切换上去轮播的，不会有太大的渲染量


### 个人改进

>- 增加组件名称wyb-noticeBar

>- 目前使用了uniUI和uViewUI两个系列组件，感觉最大问题一是他们都是优先考虑竖版，另一个就是几乎所有组件的通病，就是使用内部使用rpx定义尺寸导致不灵活，在PHP中文十三期培训中学习了父级影响子元素的两类单位:
>   - **em与rem** 通过em特殊的特性(font-size继承父级，本身margin、padding等不可继承属性则依据本身)来定义内部组件的margin、padding、position等。
>   - **百分比**  百分比通常定义width和height，再一个如背景图backgroud-size是依据块的大小来定义的，想实现 **宽高成比例自适应** ，可定义如width:60%;padding-bottom:10%来保证6:1，因为width、padding和margin都是依据父级宽度。具体可查MDN。

>- 单位的自适应。如 **rpx、px、数值和百分比自动适配** ，这里可以参考u-popup.vue中方法getUnitValue

#### 下面是修改参数说明

|参数名		|类型			|默认值		|说明			|可选值	|
|:--------:|:-------------:|:--------:|:------------:|:----:|
|width     |  String\/Number    |   100%	|   自动识别数值、百分比、auto、px和rpx字符串，默认单位是rpx   |   -   |
|height	   |  String\/Number	|   100%	|   自动识别数值、百分比、atuo、px和rpx字符串，默认单位是rpx   |   -   |
|font-size |  String/ Number	|   0.7em 	|   自动识别数值、em、px和rpx，默认单位是rpx	             |   -    |
|show-more |  Boolean	        |   false	|   是否显示查看更多图标							       |true\|false|
|noticeColor|HexColor\RgbColor\String	|  和color同色   |   通知图标颜色，rgb()、#ff0000和white关键字均可		  |-		|
|color	    |HexColor		            |  "#f5a300"    |   通告栏的整体颜色，不能使用rgb(r,g,b)				 |-		|
|bgColor    |HexColor\RgbColor\String	|  color减淡85%	 |   通告栏的背景颜色rgb()、#ff0000和white关键字均可	   |-		|