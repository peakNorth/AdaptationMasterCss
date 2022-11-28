>UI有三宝(three secrets)  透明(transparent)，阴影(shadow)加圆角(fillet)

### 透明

透明和不透明是反义词，所以二者效果一致，

#### 1.rgba设置透明

rgb 是三元色(Red（红色）Green（绿色）Blue（蓝色）)，设置自定义颜色的,
使用方法: 

```
.box{
    background-color:rgb(0,152,50)
}
```

而rgba 是设置颜色和透明度，a 是 `Alpha`,一般叫做alpha通道,alpha通道一般用作不透明度参数，
参数可以是百分比也可以是[0-1]的小数 ，0% 表示完全透明，
所以0.7表示的 30%的透明度，稍微有些透明，而不是很透明。

```
.box{
    background-color:rgba(0,152,50,0.7)
}
```

优势，任何设置颜色的都可以使用这个(rgba 替换 rgb)
缺点，必须和颜色绑定


#### 2、opacity 设置透明

opacity 就表示 不透明度

```
.box{
    opacity:0.7
}

```

同样 可以用小数也可以用百分比

优点：单独设置透明度，不耦合其他的属性
缺点：低版本的IE不适配，可能无效(IE6-IE8完全不支持 opacity,IE 使用私有的属性 filter:alpha(opacity = 70))


