# noticeBar
uniapp的通知栏组件改进

目前使用了uniUI和uViewUI两个系列组件，感觉最大问题
>- 是他们都是优先考虑竖版，
>- 几乎是所有组件的通病；就是使用内部使用rpx定义尺寸导致不灵活
>- 单位不能自动识别，如auto、数值、百分比、px、rpx等。

目前解决思路：
在PHP中文十三期培训中学习了父级影响子元素的两类单位:
>- **em与rem** 通过em特殊的特性(font-size继承父级，本身margin、padding等不可继承属性则依据本身)来定义内部组件的margin、padding、position等。
>- **百分比**  百分比通常定义width和height，再一个如背景图backgroud-size是依据块的大小来定义的，想实现 **宽高成比例自适应** ，可定义如width:60%;padding-bottom:10%来保证6:1，因为width、padding和margin都是依据父级宽度。具体可查MDN。
>- 单位的自适应。如 **rpx、px、数值、auto和百分比自动适配** ，这里可以参考u-popup.vue中方法getUnitValue
