# 移动端触摸事件及Vue-Touch 分享

1. ## 开端

> 先来一个300ms的故事

#### 移动端页面click事件响应都会慢300ms

最开始移动设备访问当都是pc上的页面，默认viewport（980px）都页面通常需要双击或
者捏开来放大以看清页面。所以设备需要判断用户是双击还是单击，safari设计来一个方案，
就是将单击事件延迟300ms，300ms内用户没有再次点击，则为单机，用户再次点击则为双击，
这个方案一直在ios上使用，后来安卓手机也借鉴来这个设计。这样'单击事件延迟300
ms'成了移动设备的规范。

？？？但300ms的延迟，总是让人不爽，如果是新闻阅读类网站有个300ms延迟倒无关紧要，
但如果是游戏又或者是在双11购物时来个300ms，很可能你的东西就被人家抢走了


#### HTML5带来了touch事件

随着HTML技术的更新迭代以及移动设备的发展壮大，原来适用与pc的交互技术远远不能满足需求，
HTML5的出现标志这移动端大行其道的时代来临，其中交互方面也带来了新的touch事件，主要包
括：touchstart、touchmove和touchend。
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
![](src/assets/oh.png)

#### 两种事件的并存带来点透的bug

由于touch事件没有延迟，而click事件有延迟，设想一个场景，上层元素touchstart后消失，300ms
后click直接传递给底层元素，这个需要与冒泡区分开，这不是冒泡，这是真真切切的点在了底层元素上


``****``


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






