# webapp开发遇到



```html
<!-- 设置宽度为设备的宽度，默认不缩放，不允许用户缩放（即禁止缩放），在网页加载时隐藏地址栏与导航栏（ios7.1新增）。 -->
<meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;" name="viewport" />
<!-- 是否启动webapp功能，会删除默认的苹果工具栏和菜单栏。 -->
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- 当启动webapp功能时，显示手机信号、时间、电池的顶部导航栏的颜色。默认值为default（白色），可以定为black（黑色）和black-translucent（灰色半透明）。这个主要是根据实际的页面设计的主体色为搭配来进行设置。 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 忽略页面中的数字识别为电话号码 -->
<meta name="format-detection" content="telephone=no, email=no" />


<!-- other -->
<!-- 启用360浏览器的极速模式(webkit) -->
<meta name="renderer" content="webkit">
<!-- 避免IE使用兼容模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">


<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-icon" sizes="76x76" href="touch-icon-ipad.png">
<link rel="apple-touch-icon" sizes="120x120" href="touch-icon-iphone-retina.png">
<link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad-retina.png">

<!-- 启动动画 -->
<link rel="apple-touch-startup-image" href="/startup.png">


// iPhone
<link href="apple-touch-startup-image-320x460.png" media="(device-width: 320px)" rel="apple-touch-startup-image" />

// iPhone Retina
<link href="apple-touch-startup-image-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

// iPhone 5
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)" href="apple-touch-startup-image-640x1096.png">

// iPad portrait
<link href="apple-touch-startup-image-768x1004.png" media="(device-width: 768px) and (orientation: portrait)" rel="apple-touch-startup-image" />

// iPad landscape
<link href="apple-touch-startup-image-748x1024.png" media="(device-width: 768px) and (orientation: landscape)" rel="apple-touch-startup-image" />

// iPad Retina portrait
<link href="apple-touch-startup-image-1536x2008.png" media="(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

// iPad Retina landscape
<link href="apple-touch-startup-image-1496x2048.png"media="(device-width: 1536px)  and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)"rel="apple-touch-startup-image" />

<!-- 选择照片 -->
<input type=file accept="image/*">
<!-- 选择视频 -->
<input type=file accept="video/*">


```


```css
body {
    margin: 0;
    -webkit-user-select: none; // 禁止选择文本
    -webkit-appearance:none; // 屏蔽阴影
    user-select: none;
    -ms-touch-action: none;
}
a, img {
    -webkit-touch-callout: none;
}
html, body, .page {
    height: 100%; width: 100%;
    overflow: hidden;
}

// border-box
element {
   width: 100%;
   padding-left: 10px;
   -webkit-box-sizing:border-box;
   box-sizing:border-box;
   border: 1px solid blue; 
}

//  css3多文本换行
p {
    overflow : hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
}

// Retina屏幕高清图片
selector {
  background-image: url(no-image-set.png);
  background: image-set(url(foo-lowres.png) 1x,url(foo-highres.png) 2x) center;
}

// position:sticky
.sticky { 
    position: -webkit-sticky; 
    position:sticky; 
    top: 15px; 
}

// 快速回弹滚动
.div {
    overflow: auto;
    -webkit-overflow-scrolling: touch;
}

// width = height
.parent {
    padding-top: 100%;
    position:relative;  
}
.children {
    width: 100%;
    vertical-align: middle;
    position: absolute;
    top: 0;
    left: 0;
    height: 100%; // 修改成对应的比率
}

```

```javascript
// html5重力感应事件
if (window.DeviceMotionEvent) { 
    window.addEventListener('devicemotion',deviceMotionHandler, false);  
} 
var speed = 30;//speed
var x = y = z = lastX = lastY = lastZ = 0;
function deviceMotionHandler(eventData) {  
  var acceleration =event.accelerationIncludingGravity;
        x = acceleration.x;
        y = acceleration.y;
        z = acceleration.z;
        if(Math.abs(x-lastX) > speed || Math.abs(y-lastY) > speed || Math.abs(z-lastZ) > speed) {
            //简单的摇一摇触发代码
            alert(1);
        }
        lastX = x;
        lastY = y;
        lastZ = z;
}
```