1. ####行内元素和块级元素?img算什么?行内元素怎么转化为块级元素?

  行内元素：和有他元素都在一行上，高度、行高及外边距和内边距都不可改变，文字图片的宽度不可改变，只能容纳文本或者其他行内元素；其中img是行元素.
  块级元素：总是在新行上开始，高度、行高及外边距和内边距都可控制，可以容纳内敛元素和其他元素；
  行元素转换为块级元素方式：display：block；
  
2. ####如何将多个元素设置为同一行?清除浮动有几种方式? 

  将多个元素设置为同一行：float，inline-block
  清除浮动的方式：
  方法一：添加新的元素 、应用 clear：both；
  方法二：父级div定义 overflow: hidden；
  方法三：利用:after和:before来在元素内部插入两个元素块，从面达到清除浮动的效果。
  .clear{zoom:1;}
  .clear:after{content:””;clear:both;display:block;height:0;overflow:hidden;visibility:hidden;}
  
3. ####怪异盒模型box-sizing？弹性盒模型|盒布局?  

  在标准模式下的盒模型：盒子总宽度/高度=width/height+padding+border+margin
  在怪异模式下的盒模型下，盒子的总宽度和高度是包含内边距padding和边框border宽度在内的，盒子总宽度/高度=width/height + margin = 内容区宽度/高度 +        padding + border + margin;
  box-sizing有两个值一个是content-box，另一个是border-box。
  当设置为box-sizing:content-box时，将采用标准模式解析计算；
  当设置为box-sizing:border-box时，将采用怪异模式解析计算。

4. ####link import两者之间区别?

  （1）老祖宗的差别，@important只能加载css
  （2）加载顺序的差别，最后加载import
  （3）兼容性的差别，老浏览器不兼容
  （4）使用dom控制样式的差别
  
5. ####href和src区别?title和alt?

  href (Hypertext Reference)指定网络资源的位置（超文本引用），从而在当前元素或者当前文档和由当前属性定义的需要的锚点或资源之间定义一个链接或者关系，在link和a 等元素上使用。
  src (Source)属性仅仅嵌入当前资源到当前文档元素定义的位置，是页面必不可少的一部分，是引入。在 img、script、iframe 等元素上使用。
  title：既是html标签，又是html属性，title作为属性时，用来为元素提供额外说明信息.
  alt：alt是html标签的属性，alt属性则是用来指定替换文字，只能用在img、area和input元素中（包括applet元素），用于网页中图片无法正常显示时给用户提供文字说明使其了解图像信息.

6. ####PNG,GIF,JPG的区别及如何选?

  GIF:
  8位像素，256色
  无损压缩
  支持简单动画
  支持boolean透明
  适合简单动画
  
  JPEG：
  颜色限于256
  有损压缩
  可控制压缩质量
  不支持透明
  适合照片
  
  PNG
  有PNG8和truecolor PNG
  PNG8类似GIF颜色上限为256，文件小，支持alpha透明度，无动画
  适合图标、背景、按钮
  
7. ####什么是FOUC?如何避免?
 
  Flash Of Unstyled Content：用户定义样式表加载之前浏览器使用默认样式显示文档，用户样式加载渲染之后再从新显示文档，造成页面闪烁。解决方法：把样式表放到文档的head

8. ####web开发中会话跟踪的方法有哪些?
  
9. ####CSS选择器有哪些
