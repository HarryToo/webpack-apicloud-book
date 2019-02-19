# vue组件

## AppHeader
> 页面标题栏（注意需要`fixStatusBar(header)`）

#### slot
slot名|说明
:--:|:--:
匿名|标题栏title
menu|标题栏右侧菜单按钮

#### prop
参数名|类型|默认值|说明
:--:|:--:|:--:|:--:
back|Boolean|true|是否显示返回按钮
color|String|'#333'|标题栏字体颜色
bg|String|'#fff'|标题栏背景色/图片
border|Boolean|true|是否显示下边线

示例:
```html
<!--带菜单按钮的标题栏-->
<app-header bg="#a1d1ff" :back="true">
    <span>我的</span>
    <i slot="menu" class="iconfont icon-refresh" @click="menuHandle"></i>
</app-header>

<!--背景图片的标题栏-->
<app-header bg="url(<%= require('./bb.jpg')%>) no-repeat top/cover" color="#fff" :border="false">关于</app-header>
```

```javascript
import {AppHeader} from '@/components/basic'

export default {
    apiready() {
        let header = $api.dom('header');
        $api.fixStatusBar(header);
    },
    vm: new Vue({
        components: {
            AppHeader
        },
        methods: {
            menuHandle(){
                app.toast('点击标题栏菜单按钮');
            }
        }
    })
}
```

## AppBody
> 页面主内容区域，better-scroll实现

#### slot
slot名|说明
:--:|:--:
匿名|内容区域

#### prop
参数名|类型|默认值|说明
:--:|:--:|:--:|:--:
pulldown|Boolean|false|是否开启下拉刷新
pullup|Boolean|false|是否开启上滑触底加载

#### event
事件名|说明
:--:|:--:
pulldown|下拉刷新
pullup|上滑加载

示例:
```html
<!--使用AppBody组件，外层dom的id须为view-->
<div id="view">
    <app-header :back="false">首页</app-header>
    <app-body :pulldown="true" @pulldown="getData" :pullup="true" @pullup="loadMore">
        <div class="content">内容...</div>
    </app-body>
</div>
```

## AppSwiper
> 轮播组件，[Swiper](https://www.swiper.com.cn/api/index.html)实现

#### slot
slot名|说明
:--:|:--:
匿名|轮播slide列表区域（配合AppSlide组件）

#### prop
参数名|类型|默认值|说明
:--:|:--:|:--:|:--:
loop|Boolean|true|是否首尾相接循环
auto-play|Boolean \| Object|true|是否自动切换，参见[原配置](https://www.swiper.com.cn/api/autoplay/16.html)
slide-space|Number \| String|1|slide间隙，支持百分比
slide-index|Number|0|初始slide下标
slide-center|Boolean|false|slide是否居中
slide-view|Number|1|同时展示slide数
slide-group|Number|1|每组slide数
pagination|Boolean|false|是否显示页码小圆点

示例:
```html
<app-swiper :slide-index="1" :slide-center="true" slide-space="4%" :slide-view="1.2">
    <app-slide><img src="<%= require('./img1.png') %>" alt=""></app-slide>
    <app-slide><img src="<%= require('./img1.png') %>" alt=""></app-slide>
    <app-slide><img src="<%= require('./img1.png') %>" alt=""></app-slide>
</app-swiper>
```