>UI有三宝(three secrets)  透明(transparent)，阴影(shadow)加圆角(fillet)

### 圆角

css 中圆角不是 fillet,而是 `border-radius` ,表示边界的半径

#### border-radius 50% 100%

border-radius 是以下几个的简写

border-top-left-radius
border-top-right-radius
border-bottom-right-radius
border-bottom-left-radius


基本格式
border-radius: top-left  top-right bottom-right bottom-left;

top-left 上左
top-right 上右
bottom-right 下右
bottom-left 下左
顺时针方向,值可以是10px（代表半径）,50%()

```
border-radius: 1px 1px 1px 1px ;
```

原理解析：
10px比较好理解，就是指定半径的圆和直角相切。

这个百分比是表示盒子的长宽按比例换算的长度为半径的一个椭圆,然后和直角相切,
所以圆角并不一定延伸到具体的某个固定点。

而有时候发现50%和100%是一样(比如四个角都是相同的且大于50%)，有时候又不一样(单独一个角示例)，

其实这个是因为角冲突了的关系，也就是两个角的半径之和已经大于了盒子的长度（长或宽），没法渲染成一个完整的图形了
（如果强制占用长度的一般的话，显示会有锐角，或者其他奇怪的形状）
所以浏览器的处理方式是两个角对应的圆形的半径同比缩小，直到不冲突（两个圆的切点在盒子的边框上）

这个冲突的解决方式是不分百分比或者px的,只是百分比更容易出现，所以你可能你可能明显的发现有些角半径变小了


额外知识点：
1、画一个圆非常简单，只需要一个正方形，然后百分比都为50%即可,椭圆类似
2、画一个三角形也非常简单，只需要设置border 即可
```
    .border-radius-triangle {
        background-color: rgba(38, 220, 220, 0);
        width: 0;
        height: 0;
        border: 40px solid;
        border-width: 10px 40px 180px 20px;
        border-color: transparent transparent red transparent;
    }
```

