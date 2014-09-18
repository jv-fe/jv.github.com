# JVC v0.1
JVC是JV前端团队初步制定的一套CSS命名规范，引鉴于[NEC]。  
这套规范有助于提高代码的可读性，减少命名冲突。


## 命名连字符（减号）"-"
有两种含义：  
1. 分类前缀分隔符  
2. 扩展分隔符

## 分类前缀
### 1.布局(grid)（.g-），用于分隔页面不同区块，如页面的头部，主体和脚部。
```html
<div class="g-hd">...</div>
<div class="g-mn">...</div>
<div class="g-ft">...</div>
```
```css
.g-hd{}
.g-mn{}
.g-ft{}
```
### 2.模块(module)（.m-），用于页面具体的模块。如下图布局  
![module:layout][layoutImg]  
html对应的class命名可以为：  
```html
<body>
    <div class=“g-hd”>
    	<div class=“m-logo”></div>
    </div>
    <div class=“g-sd”>
    	<div class=“m-search”></div>
    	<div class=“m-account”></div>
    	<div class=“m-navi”></div>
    	<div class=“m-featItem”></div>
    </div>
    <div class=“g-mn”>
    	<div class=“m-signUp”></div>
    	<div class=“m-featImg”></div>
    	<div class=“g-news”>
            <div class=“m-news”></div>
            <div class=“m-news”></div>
    	</div>
    </div>
</body>
```
再如导航模块，新闻列表模块和图片轮播模块，可分别命名为.m-nav，.m-newsList和.m-galleryPlayer。
### 3.页面挂件(widget)（.w-），理解为比模块(.m-)更小的元素或区块。如下图的搜索框  
![widget:search][searchImg]  
```html
<form class=“w-search” action=“http://www.google.com.hk/search”>
    <input type=“text” name=“keyword” class=“keyword” />
    <input type=“submit” value=“search” class=“btn”/>
</form>
```
```css
.w-search{}
.w-search .keyword{}
.w-search .btn{}
```
再如页面的标题，页面的次导航和页面的翻页控件，可分别命名为.w-title，.w-subNav和.w-pageTurn。
### 4.通用组件(common)（.c-），多个页面公用的组件。如下图的分享通用组件  
![common:share][shareImg]   
```html
<dl class=“c-share”>
    <dt>分享到：</dt>
    <dd>
        <a href=“”>新浪微博</a>
        <a href=“”>腾讯微博</a>
        ...
    </dd>
</dl>
```
```css
.c-share{}
.c-share dt{}
.c-share dd{}
.c-share a{}  /* 注：用后代选择器容易污染子元素，尽量使用class选择器代替后代选择器。后面也有说明。 */
```
再如公用登录组件，分享组件和弹窗组件，可分别命名为.c-login，.c-share和.c-popup。  
### 5.元件(unit)（.u-），页面上小得不可再划分的元件，多用于页面的图标和按钮。   
如页面logo，列表前的小图标和游戏下载的按钮，可分别命名为.u-logo，.u-listIcon和.u-gameDownload。
```html
<a class="u-logo" href="\">logo</a>
<span class="u-listIcon" ></span>
<a class="u-gameDownload" href="">游戏下载</a>
```
### 6.功能(function)(.f-)，样式功能类或常用解决方案。如
```css
/* 清除浮动 */
.f-cb{*zoom:1;}
.f-cb:after {clear:both;content: ".";display: block;height:0;overflow:hidden;}
/* 隐藏元素 */
.f-dn{display:none;}
```
个人也可将使用率较高的样式剥离出来，如
```css
/* 首行缩进 */
.f-ti{text-indent:2em;}
/* 单行溢出显示省略号 */
.f-toe{overflow:hidden;word-wrap:normal;white-space:nowrap;text-overflow:ellipsis;}
/* 使用图标字体 */
.f-iconFont{font-family:'heros_icon';}
```
### 7.脚本(javascript)（.j-），用于脚本获取dom节点。
```html
<div class="m-weatherInfo" id="j-weather"></div>
```
```javascript
var $weather = $("#j-weather");
```

## 分类扩展  
以上分类除了脚本分类（.j-）都可以在命名后面再加上连字符（减号）"-"，表示该分类的一个扩展。  
扩展的名字最好是有语义的英文：
```html
<dl class=“w-share”>
    <dt>分享到：</dt>
         <dd>
            <a class=“u-ico u-ico-weibo” href=“”>新浪微博</a>
            <a class=“u-ico u-ico-txweibo” href=“”>腾讯微博</a>
            <a class=“u-ico u-ico-yixin” href=“”>易信</a>
            <a class=“u-ico u-ico-weixin” href=“”>微信</a> 
            <a class=“u-ico u-ico-tieba” href=“”>贴吧</a>
     </dd>
</dl>
```
```css
.u-ico{display:inline-block;width:15px;height:15px;margin-right:8px;text-indent:-9999px;background:url(../sprite.png) -9999px -9999px no-repeat;}
.u-ico-weibo{background-position:0 0;}
.u-ico-weibo:hover{background-position:0 -20px;}
.u-ico-txweibo{background-position:-20px 0;}
.u-ico-txweibo:hover{background-position:-20px -20px;}
```
扩展的名字也可以是简单的数字，如
```html
<div class=“m-newsList m-newsList-1”>…</div>
<div class=“m-newsList”>…</div>
<div class=“m-newsList”>…</div>
```
```css
/* 模块通用样式 */
.m-newsList{color:black;}
/* 扩展样式 */
.m-newsList-1{color:blue;}

```

## 注意要点
* 使用驼峰式写法，便于阅读。
* 不以ID定义样式，因为ID具有唯一性，不可复用。
* 尽量使用class选择器代替后代选择器，防止子元素被污染和更好地解耦了html和css。

## 错误例子
```css
.class{}
/* 不要以一个没有类别的样式作为主选择器，这样的选择器只能作为后代选择器使用，比如.m-xxx .class{}。 */

.g-xxx .class{}
/* 不要在页面布局中使用后代选择器，因为这个后代选择器可能会污染里面的元素。 */

.g-xxx .m-yyy{}
.g-xxx .u-yyy{}
/* 不要用布局去控制模块或元件，模块和元件应与布局分离独立。 */

.m-xxx .f-xxx{}
.m-xxx .s-xxx{}
/* 不要通过模块或其他类来重定义或修改或添加已经定义好的功能类选择器和皮肤类选择器。 */

.m-xxx .m-yyy .zzz{}
/* 不要越级控制，如果.zzz是.m-yyy的后代选择器，那么不允许.m-yyy之外的选择器控制或修改.zzz。 */
/* 此时可以使用.m-yyy的扩展来修改.zzz，比如.m-yyy-1 .zzz{}。 */
```

## 范例
```css
/* reset & base */

/* --- function --- */
.f-cb{*zoom:1;}
.f-cb:after{content:".";display:block;height:0;overflow:hidden;clear:both;}
.f-dn{display:none;}

/* --- grid --- */
/* 头部 */
.g-hd{position:relative;z-index:1;height:668px;width:960px; margin:0 auto;}
/* 主体 */
.g-bd{position:relative;height:1326px;background:url(http://hearthstone.nos.netease.com/3/minisite/gold/bd-m.jpg) 50% 0 no-repeat;}

/* --- module --- */
/* 导航模块 */
.m-nav{position:relative;height:145px;overflow:hidden;}
.m-nav .txt1{position:absolute;top:60px;font-size:20px;font-weight:700;color:#ffecb6;}
.m-nav .txt1-1{left:258px;}
.m-nav .txt1-2{left:460px;}
.m-nav .txt1-2{left:460px;}
.m-nav .txt1-3{left:670px;}
/* 新闻列表模块 */
.m-news{float:right;width:402px;height:411px;}
.m-news .newsList{margin-top:5px;height:288px;}
.m-news .txt1{margin-left:10px;line-height:34px;color:#302115;font-size:14px;border-bottom:1px solid #f2e4bf;}
.m-news .wrap{padding-right:3px;border-bottom:1px solid #d7be8a;}
.m-news .ct{float:left;width:340px;height:35px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;color:#302115;}
.m-news .ct:hover{color:#ae300e;}
.m-news .date{display:block;padding-left:350px;text-align:right;}

/* --- unit --- */
.u-ico,.u-logo,.u-abtn,.u-bigBtn{background:url(http://hearthstone.nos.netease.com/3/minisite/gold/sprite.png) -9999px -9999px no-repeat;}
/* 标题前面icon */
.u-ico-1{display:inline-block;width:51px;height:51px;background-position:0 -130px;vertical-align:middle;margin-right:10px;}
/* 视频icon */
.u-ico-video{display:inline-block;width:17px;height:18px;background-position:-60px -130px;vertical-align:middle;margin-right:5px;}
/* logo */
.u-logo{position:absolute;left:220px;top:80px;width:250px;height:95px;}
/* 查看更多按钮 */
.u-abtn-more{float:right;margin-top:20px;width:150px;height:45px;line-height:40px;text-align:center;font-size:14px;font-weight:700;color:#fff;background-position:-140px 0;}
.u-abtn-more:hover{background-position:-140px -50px;}
/* 进入官网button和下载游戏button */
.u-bigBtn{float:left;width:272px;height:70px;margin-right:80px;}
.u-bigBtn-1{background-position:0 -350px;}
.u-bigBtn-1:hover{background-position:0 -430px;}
.u-bigBtn-2{background-position:0 -190px;}
.u-bigBtn-2:hover{background-position:0 -270px;}
/* 折叠按钮 */
.u-collapse{position:absolute;right:60px;top:75px;width:82px;height:27px;background:url(http://hearthstone.nos.netease.com/3/common/collapse-button.png) -9999px -9999px no-repeat;}
.u-collapse-unfold{background-position:-20px -36px;}
.u-collapse-unfold:hover{background-position:-20px -108px;}
.u-collapse-fold{background-position:-20px 0px;}
.u-collapse-fold:hover{background-position:-20px -72px;}
```
## PS
分类前缀可根据团队来增加或修改，有什么建议或问题可随时提出。


[NEC]:http://nec.netease.com/
[layoutImg]:https://raw.githubusercontent.com/yikfun/JVC/master/images/layout.jpg
[searchImg]:https://raw.githubusercontent.com/yikfun/JVC/master/images/search.png
[shareImg]:https://raw.githubusercontent.com/yikfun/JVC/master/images/share.png
[blzLoginImg]:https://raw.githubusercontent.com/yikfun/JVC/master/images/blzLogin.png
