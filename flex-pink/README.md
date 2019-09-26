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


# flex布局子项常用属性
  + flex子项目占的份数
    + flex:1
  + align-self子项自己控制在侧轴的排列方式
    + 操作局部的子盒子
  + order属性定义子项的先后顺序
    + 数字越小,排列越靠前
    + 默认是0


# 圣杯布局
  + 左右固定宽度,中间自适应
  + div:nth-child(1)
```
section {
  display: flex;
  width: 60%;
  height: 150px;
  background-color: pink;
  margin: 0 auto;
}

section div:nth-child(1) {
  width: 100px;
  height: 150px;
  background-color: red;
}

section div:nth-child(2) {
  flex: 1;
  background-color: green;
}

section div:nth-child(3) {
  width: 100px;
  height: 150px;
  background-color: blue;
}
```

# 常用初始化样式
  + body
```
body {
    max-width: 540px;
    min-width: 320px;
    margin: 0 auto;
    font: normal 14px/1.5 Tahoma, "Lucida Grande", Verdana, "Microsoft Yahei", STXihei, hei;
    color: #000;
    background: #f2f2f2;
    overflow-x: hidden;
    -webkit-tap-highlight-color: transparent;
}
```

# 顶部固定搜索框样式
```
.search-index {
    /* 固定定位和父元素无关,以屏幕为准 */
    /* 因此需要限制固定定位的宽 */
    position: fixed;
    top: 0;
    left: 50%;
    -webkit-transform: translateX(-50%);
    transform: translateX(-50%);
    width: 100%;
    max-width: 540px;
    min-width: 320px;
    height: 44px;
    background-color: pink;
}
```





# 将一个元素改为绝对定位
  - 其内部的margin属性将失效
  - 其父元素的position应改为positive
  - 伪类元素(.search::before)的父节点是.search

# 让元素在y轴方向垂直
  - 如果是css3的和盒模型
  - 比如高度为26px,上下变框宽度各为1px.
  - 应设置line-height:24px
  - 如果是之前的盒模型应让 height = line-height


# 指定图片为背景
  - 不偏移
```
background: url('../images/hotel.png') no-repeat 0 0;
```
  - 靠底端对齐,水平居中
```
background: url('../images/hotel.png') no-repeat bottom center;
```

# 背景的线性渐变
  - 语法(需要带浏览器的私有前缀)
```
background: linear-gradient (起始方向, 颜色1, 颜色2, ...);
```
  -从左边开始,由红变蓝
```
background: -webkit-linear-gradient(left, red, blue);
```
  - 从左上开始,由红变蓝
```
background: -webkit-linear-gradient(left top,red, blue);
```

# 三角箭头的制作:
  - 显示一个正方形的上边框和右边框
  - 使用transform旋转45度
```
.more::after{
  width:7px;
  height:7px;
  border-top:2px solid #fff;
  border-right: 2px solid #fff;
  transform: routate(45deg);
}
```
#