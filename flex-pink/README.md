# flex布局原理
  - 当我们为父盒子设为flex布局以后,子元素的float、clear和vertical-align属性将失效
  - 通过给父盒子添加flex属性,来控制子盒子的位置和排列方式
  - 元素是跟着主轴排列的

# flex布局父项常见属性
  - 主轴,默认是x轴
  - flex-direction: 设置主轴的方向
    + row: 默认值从左到右
    + row-reverse: 从右到左
    + column: 从上到下
    + column: 从下到上
  - justify-content(调整内容): 设置主轴上的子元素排列方式
    + flex-start:默认值从头部开始,如果主轴是x轴,则从左到右
    + flex-end:从尾部开始排列
    + center:在主轴居中对齐 (如果主轴是x轴,则水平居中)
    + space-around:平分剩余空间(margin-left和margin-right都相同)
    + space-between:先两边贴边再平分剩余空间(margin-left和margin-right都相同,但是最左边没有左外边距,最右边没有右外边距)
  - flex-wrap: 设置子元素是否换行
    + 默认的子元素是不换行的
    + wrap: 换行.
  - align-content: 设置侧轴(y)上的子元素的排列方式(多行)
    + flex-start:(默认值)在侧轴的头部开始排列
    + flex-end:在侧轴的尾部开始排列
    + center:在侧轴中间显示
    + space-around:在侧轴平分剩余空间
    + space-between: 在侧轴先分布在两头,再平分剩余空间
    + stretch:默认值(子元素平分父元素的高度or宽度)
  - align-items: 设置侧轴上的子元素的排列方式(单行)
    + flex-start:从上到下
    + flex-end:从下到上
    + center:垂直居中
    + stretch:拉伸(默认值,子元素不指定高度时,子元素和父元素高度一样)
  - flex-flow: 符合属性,相当于同时设置了flex-direction 和 flex-wrap

# 使用flex让div元素垂直居中
```
div{
  display:flex;
  justify-content:center;
  align-items:center;
}
div span{
  ...
}
```