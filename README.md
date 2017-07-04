# 移动端触摸事件及Vue-touch分享

## 1. 开端

> 先来一个300ms的故事

#### 移动端页面click事件响应都会慢300ms

最开始移动设备访问当都是pc上的页面，默认viewport（980px）都页面通常需要双击或者捏开来放大以看清页面。所以设备需要判断用户是双击还是单击，safari设计来一个方案，就是将单击事件延迟300ms，300ms内用户没有再次点击，则为单击，用户再次点击则为双击，这个方案一直在ios上使用，后来安卓手机也借鉴来这个设计。这样'单击事件延迟300ms'成了移动设备的规范。

？？？但300ms的延迟，总是让人不爽，如果是新闻阅读类网站有个300ms延迟倒无关紧要，但如果是游戏又或者是在双11购物时来个300ms，很可能你的东西就被人家抢走了


#### HTML5带来了touch事件

随着HTML技术的更新迭代以及移动设备的发展壮大，原来适用与pc的交互技术远远不能满足需求，HTML5的出现标志这移动端大行其道的时代来临，其中交互方面也带来了新的touch事件(支持多点触控)，主要包括：touchstart、touchmove和touchend。
* touchstart事件：当手指触摸屏幕时候触发，即使已经有一个手指放在屏幕上也会触发。

* touchmove事件：当手指在屏幕上滑动的时候连续地触发。在这个事件发生期间，调用
preventDefault()事件可以阻止滚动。

* touchend事件：当手指从屏幕上离开的时候触发。

* touchcancel: 系统取消touch时触发，一般不使用。

这里需要注意一下，touch事件没有延迟，touch 事件推出后，在移动端设备中，touch和click事件是并存的

那么我们丛touch事件能得到什么呢？
```
touches：表示当前跟踪的触摸操作的touch对象的数组。

targetTouches：特定于事件目标的Touch对象的数组。

changeTouches：表示自上次触摸以来发生了什么改变的Touch对象的数组。

```
一个touch对象包含：
```
{
    screenX: 511,
    screenY: 400,//触点相对于屏幕左边沿的Y坐标
    clientX: 244.37899780273438,
    clientY: 189.3820037841797,//相对于可视区域
    pageX: 244.37,
    pageY: 189.37,//相对于HTML文档顶部，当页面有滚动的时候与clientX=Y 不等
    force: 1,//压力大小，是从0.0(没有压力)到1.0(最大压力)的浮点数
    identifier: 1036403715,//一次触摸动作的唯一标识符
    radiusX: 37.565673828125, //能够包围用户和触摸平面的接触面的最小椭圆的水平轴(X轴)半径
    radiusY: 37.565673828125,
    rotationAngle: 0,//它是这样一个角度值：由radiusX 和 radiusY 描述的正方向的椭圆，需要通过顺时针旋转这个角度值，才能最精确地覆盖住用户和触摸平面的接触面
    target: {} // 此次触摸事件的目标element
}
```
![](src/assets/oh.jpeg)

#### 两种事件的并存带来点透的bug（幽灵点击）

由于touch事件没有延迟，而click事件有延迟，设想一个场景，上层元素touch后消失，300ms后click直接传递给底层元素，这个需要与冒泡区分开，这不是冒泡，这是真真切切的点在了底层元素上



## 2. 解决方案

> 有问题总要解决的吧

#### 300毫秒如何干掉？

1. 设置不能缩放：user-scalable=no。 不能缩放就不会有双击缩放操作，因此click事件也就没了300ms延迟，这个是Chrome首先在Android中提出的。
2. 设置显示宽度：width=device-width。包含 width=device-width 或者置为比 viewport 值更小的页面上会禁用双击缩放。当然，没有双击缩放就没有 300 毫秒点击延迟。
3. 以上其实可以归纳为```<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">```
4. FastClick, FastClick是 FT Labs 专门为解决移动端浏览器 300 毫秒点击延迟问题所开发的一个轻量级的库。简而言之，FastClick 在检测到 touchend事件的时候，会通过 DOM 自定义事件立即触发一个模拟click事件，并把浏览器在 300 毫秒之后真正触发的 click事件阻止掉。

#### 幽灵点击怎么办？

1. 上下层都用touch事件模拟
2. 缓动动画延迟消失
3. FastClick



## 3. 这样我们就满足了吗？

过去用鼠标只能点点，但乔布斯给我买带来了多点触摸，难道还是只能点点吗？而且单纯用touchstart或者touchend模拟点击的体验很差，这样的情况下，各种手势库应运而生，hammer.js就是其中但优秀的库之一，当下较火的前段框架vue也不甘落后，带来了vue-touch，基于hammer.js的二次封装，好吧，下面我们进入触摸的世界

## 进入[Vue-touch](https://github.com/vuejs/vue-touch)


## Build Setup
[//]: <分割线>
***

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```






