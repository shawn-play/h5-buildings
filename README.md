# h5 buildings
结合[*animate.css*](https://daneden.github.io/animate.css/), [*wow.js*](http://mynameismatthieu.com/WOW/), [*swiper.js*](http://www.swiper.com.cn/)搭建的H5页面的前端开发环境

## 先看一个基于此项目开发的[一个案例](http://eomanager.catcherchina.com/)
此项的目的是，结合wow和swiper搭建一个能够快速开发上线静态H5项目的前端开发环境，提高效率
### 1. 关于animate.css,wow.js和swiper.js
*animate.css*是一个开源的包含了很多css3关键帧动画的库样式表，你可以在其官网上查到很多的动画效果，完全能满足一般H5页面的动画效果。


*wow.js*是一个控制关键帧动画播放的js库，无压缩版只有14kb，小巧实用，不过我们可能会遇到一些问题，这里不表。


*swiper.js*应用非常广泛的轮播库，功能十分的强大，几乎能满足所有H5的切换需求、事件响应等等。
### 2. 在组织代码之前，先掌握以下基本用法


animate.css, 先看一段aniamte支持的css3动画的代码
```
@-webkit-keyframes pulse {
  ...
}
@keyframes pulse {
  ...
}
.pulse {
  -webkit-animation-name: pulse;
  animation-name: pulse;
}
```

```
<img src="..." class="pulse" >
```
这样就可以让<img>执行相应的动画


wow.js, wow.js通过dom上的data-wow-*属性来控制动画，而这些 * 属性与 css3 animate支持的属性相同, 包括：delay,duration,iteration...
```
<img class="pulse wow" data-wow-delay="1s" data-wow-duration="2s" data-wow-iteration="infinite" >
<sctipt>
    new WOW().init();
</script>
```
以上代码，class=wow 使当前元素受wow.js控制，当执行new WOW().init()时，元素延迟1秒开始, 用2秒时间完成.pulse动画，次数无限循环；使用new WOW().init()的时机是一个问题，这里不表！


swiper.js, swiper官方文档已经十分清楚，不在赘述.
```
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">page1</div>
    <div class="swiper-slide">page2</div>
  </div>
</div>
<script>
var mySwiper = new Swiper('.swiper-container', {
  direction: 'vertical',
  loop: false
});
//禁止swiper滑动翻页
mySwiper.detachEvents();
$(selector).on('click', function() {
  //翻页时调用wow，重置帧动画
  new WOW().init();
  setTimeout(function () {//异步，保证翻页后，帧动画被重置
    mySwiper.slideNext();
  },0)
})
</script>
```
