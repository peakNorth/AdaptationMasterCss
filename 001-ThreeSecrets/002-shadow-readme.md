>UI有三宝(three secrets)  透明(transparent)，阴影(shadow)加圆角(fillet)

### 阴影

css 中支持文字阴影(text-shadow)和容器阴影(box-shadow)

#### 1.text-shadow 文字阴影


基本格式
text-shadow: offset-x offset-y blur-radius color;

offset-x 水平偏移
offset-y 垂直偏移
blur-radius 模糊半径
color 阴影颜色

```
text-shadow: -2px -2px 2px red;
```

原理透析: 
就是复制原本的文本，加以移动并处理(模糊和颜色)
如果不加模糊半径 和 颜色，把水平偏移和垂直偏移设置大值，就很明显的发现就是一模一样的文本
模糊实现` filter: blur(1px);` ,颜色实现 `color: brown;` 不是font-color 什么的，就是 `color` 属性就表示字体颜色
所以这个应该可以类比为`语法糖`. css的东西都非常好用的原因之一,
>注意:text-shadow创造出来的文本不被认定为文本，所以你无法直接复制它(想想为什么，如果能复制，那么你可能复制的文案就是两个一样的内容)


额外知识:
1、可以支持配置多个，用`,`分开即可

```
text-shadow: -2px -2px 2px red, 2px 2px 2px rgb(28, 216, 97);
```

2、任何node都可以用，表示的是里面的文字做阴影处理，而不是部分标签独有的属性


#### 2.box-shadow 容器阴影

基本格式
text-shadow: offset-x offset-y blur-radius spread-radius color inset;

参数解释:
支持和文本阴影一样，水平偏移，垂直偏移，模糊半径，不过增加了两个可选参数， 拓展半径(spread-radius)和 插入内部 (inset)

spread-radius 取正值 阴影扩大，取负值阴影缩小 
inset 不指定则默认向外，指定则向内扩散，背景之上、内容之下

原理透析：
水平偏移->垂直偏移 ->半径变化->插入方向判断->模糊处理
只设置水平偏移和垂直偏移的话，颜色是黑色的，说明只复制了原来的盒子的大小

额外的知识：
1、inset 只要不放在数字中间都可以识别(inset 30px -30px 0px red, 30px -30px 0px inset red,30px -30px 0px  red inset)
这可能和css识别有关系

2、inset 看起来不直观？使用 inset 的时候，其实和在外面一样，取两个容器的重叠部分不处理，未重叠的部分变成阴影(而不是重叠的部分)

3、如果要实现比较逼真的立体效果，可以叠加阴影来强化

```
box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 30px 0 rgba(0, 0, 0, 0.19);
```