# vue指令

## v-cache
> 图片缓存（只在生产环境下启用）

示例:
```html
<li v-for="item,index in list" :key="item.id">
    <img v-cache="item.img_url" alt="">
    <p>{% raw %}{{item.title}}{% endraw %}</p>
</li>
```