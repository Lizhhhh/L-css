# rem 基础(root em)
  - 是一个单位
  - 相对于html元素字体大小来说的

# 媒体查询(Media Query)
  - 是CSS3新语法
  - 使用@media查询,可以针对不同的媒体类型定义不同的样式
  - 当你重置浏览器大小的过程中,也能也会根据浏览器的宽度和高度重新渲染页面
  - 用法如下
```
@media mediatype and|not|only (media feature) {
  CSS-Code;
}
```
  - 说明:
    - 1.用@media开头,
    - 2.mediatype 媒体类型
      + all:用于所有设备
      + print:用于打印机和打印预览
      + screen:用于电脑屏幕,平板电脑,智能手机等
    - 3.关键字 and | not | only
      + and:且
      + not:非
      + only:指定某个特定的媒体类型,可以省略
    - 4.媒体特性(media feature)必须用小括号包含
      + width:定义输出设备中页面可见区域的宽度
      + min-width:定义输出设备页面最小可见区域宽度
      + max-width:定义输出设备页面最大可见区域宽度

  - 栗子:
```
<style>
    /* 1.媒体查询一般按照从小到大的顺序来 */
    /* 2. x <540px */
    @media screen and (max-width: 539px) {
        body {
            background-color: blue;
        }
    }

    /*  540px <= x < 969px; */
    @media screen and (min-width: 540px) {
        body {
            background-color: green;
        }
    }

    /* x >= 970px */
    @media screen and (min-width: 970px) {
        body {
            background-color: red;
        }
    }
</style>
```

# 引入资源(理解)
  - 当样式比较繁多的时候,我们可以针对不同的媒体使用不同的stylesheets(样式表)
  - 在link中判断设备的尺寸,然后引入不同的css文件
  - 语法规范如下
```
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.css">
```
  - 针对不同的屏幕尺寸,调用不同的css文件


# less 基础
  - css是一门非程序语言:
    - 1. 无变量、函数、作用域等概念
    - 2. CSS需要书写大量看似没有逻辑的代码,CSS冗余度高
    - 3. 不方便维护及扩展,不利于复写
    - 4. 没有很好的计算能力
    - 5. 非前端工程师,很难写出组织良好且易于维护的CSS项目

  - less(Leaner Style Sheets的缩写) 是一门CSS扩展语言,也成为CSS预处理器
  - 在现有的CSS语法上,为CSS加入程序式语言的特性
  - 引入了变量、Mixin(混入)、运算以及函数等功能,大大简化了CSS的编写
  - Less官网: http://lesscss.cn/

  - less使用:
    - Less变量
    - Less编译:
      + less文件需要编译成为css文件,才能让html页面使用
      + vscode下载: easy less
    - Less嵌套
      + 交集|伪类|伪元素选择器
        - 内层选择器的前面没有&符号,则它被解析为父选择器的后代
        - 如果有&符号,它就被解析为父元素自身或父元素的伪类
    - Less运算
      + 1. 运算符的左右必须敲用一个空格隔开
      + 2. 两个参与运算的参数,如果只有一个数有单位,则最后的结果就以这个单位为准
      + 3. 两个参与运算的参数,如果2个数都有单位,且单位不一样.则以第一个为准

# rem适配方案
  - 1. 让一些不能等比自适应的元素,达到当设备尺寸发生改变的时候,等比例适配当前设备
  - 2. 使用媒体查询根据不同设备按比例设置html的字体大小,然后页面元素使用rem做尺寸单位,当html字体大小变化元素尺寸也会发生变化,从而达到等比缩放的适配

  # 技术方案1
    - less
    - 媒体查询
    - rem

  # 技术方案2
    - flexible.js
    - rem

# 常见尺寸宽度
  - iphone 4、5
    - 640px
  - iphone 6、7、8
    - 750px
  - Android
    - 常见320px、360px、375px、384px、400px、414px、500px、720px
    - 大部分你4.7~5寸的安卓设备为720px

# 动态设置html标签font-size大小
  - 1. 假设设计稿是750px
  - 2. 假设我们把整个屏幕划分为15等分(也可以是10等份、20等份)
  - 3. 每一份作为html字体大小,这里就是50px
  - 4. 在320px设备的时候,字体大小为320/15就是21.33px
  - 5. 用页面元素的大小除以不同的html字体大小就会发现他们比例还是相同的
  - 6. 比如以750为标准设计稿
  - 7. 一个100*100像素的页面元素在750屏幕下,就是100/50转换为rem是2rem * 2rem比例是 1比1
  - 8. 320屏幕下,html字体大小为21.33则2rem = 42.66px, 此时的宽高都是 42.66 但是宽和高的比例还是1比1
  - 9. 实现了页面元素盒子等比例缩放的效果


# 给body指定样式(常规)
```
body {
    min-width: 320px;
    width: 15rem;
    margin: 0 auto;
    line-height: 1.5;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #f2f2f2;
}
```

# 头部固定定位
  - 1. 固定定位position:fixed, margin和padding失效
  - 2. 使用left、top来调整元素的位置
  - 3. 使用transform: translateX(-50%)往回走盒子宽度的一半
```
.search-content{
  position:fixed;
  top:0;
  left:50%;
  transform: translateX(-50%);
  width:15rem;
  height: 88rem / 50;
  background-color: #ffc001;
}
```

# 取消input框周围的蓝色边框
```
input {
  outline: none;
}
```

# 简洁高效的rem适配方案flexible.js
  - github:https://github.com/amfe/lib-flexible
  - 我们要做的,就是确定好我们当前设备的html文字大小
  - 如设计稿是750px,那么我们只需把html文字大小设置为75px即可

