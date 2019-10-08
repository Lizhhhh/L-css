# 建立目录结构,和index.html

# index.html的初始化
  - 1.设置视口(使用推荐的视口设置)
```
<meta name="viewport" content="width=device-width, initial-scale=1.0,user-scalaable=no, maximum-scale=1.0,minimum-scale =1.0">
```
  - 2.导入normalize.css初始化样式
      - 下载网址:http://necolas.github.io/normalize.css/
      - 导入
```
<!-- 引入css的初始化文件 -->
<link rel="stylesheet" href="css/normalize.css">
```

# body初始化样式
```
body{
  margin:0 auto;
  min-width: 320px;
  max-width: 640px;
  background: #fff;
  font-size: 14px;
  font-family: -apple-system, Helvetica, sans-serif;
  line-height:1.5;
  color:#666;
}
```

# 二倍精灵图做法:
  - 1. 在firework里面把精灵图等比例缩放为原来的一半
  - 2. 根据大小测量坐标
  - 3. 在代码里面background-size也要写:精灵图原来高度的一半
