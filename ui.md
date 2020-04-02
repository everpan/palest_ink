慕课:手把手带你打造自己的UI样式库

[课程介绍]: http://www.imooc.com/read/36/article/382 "title"  这个是什么

[http://www.imooc.com/read/36/article/382]

####框架的好处
标准化
提高开发效率
方便扩展
提高页面加载速度
####现有移动UI
Bootstrap WeUI[微信] VUE-X 

##盒模型
高宽，width/height
内边距 padding
边框 border 只支持绝对宽度
外边距 margin：如果两个盒子都设置了 margin，在排列这两个盒子的时候并不会把两个 margin 值的和作为两个盒子的间距，相邻取最大值作为margin；外边距折叠，就是折叠了小值的边距；
横向空间：width  + padding宽度 + border宽度
纵向空间：height + padding宽度 + border宽度
box-sizing 控制box宽高计算方式
content-box:
border-box: IE历史模型，宽高为整个box的宽高

##文档流
块元素，每行一个
行元素，一行，依次从左到右
绝对定位，固定定位 absolute/fixed，脱离文档流
浮动属性 float 覆盖移动方式
z-index 只对已经有定位的元素生效（position:relative/absolute/fixed）



