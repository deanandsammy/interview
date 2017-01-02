1. 行内元素和块级元素?img算什么?行内元素怎么转化为块级元素?

  行内元素：和有他元素都在一行上，高度、行高及外边距和内边距都不可改变，文字图片的宽度不可改变，只能容纳文本或者其他行内元素；其中img是行元素.
  块级元素：总是在新行上开始，高度、行高及外边距和内边距都可控制，可以容纳内敛元素和其他元素；
  行元素转换为块级元素方式：display：block；
  
2. 如何将多个元素设置为同一行?清除浮动有几种方式? 

  将多个元素设置为同一行：float，inline-block
  清除浮动的方式：
  -方法一：添加新的元素 、应用 clear：both；
  -方法二：父级div定义 overflow: hidden；
  -方法三：利用:after和:before来在元素内部插入两个元素块，从面达到清除浮动的效果。
  .clear{zoom:1;}
  .clear:after{content:””;clear:both;display:block;height:0;overflow:hidden;visibility:hidden;}
