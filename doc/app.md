## resolvePath(url)
> 根据开发/生产环境解析页面文件绝对路径

返回值类型: String
#### url
类型|默认值|说明
:--:|:--:|:--:
String|-|页面相对src/views/下路径

示例:
```javascript
// 打开页面：src/views/about/about.html
api.openWin({
    name: 'about',
    url: app.resolvePath('about')
});
```

## toast(msg)
> 文字消息提示框，`api.toast()`封装

#### msg
类型|默认值|说明
:--:|:--:|:--:
String|-|提示消息文字

示例:
```javascript
app.toast('hello!');
```

## alert(option)
> dialogBox弹窗模块封装

#### option
字段|类型|默认值|说明
:--:|:--:|:--:|:--:
title|String|'提示'|标题文字
content|String|'内容'|内容文字
btn|Array&lt;String&gt;|\['确定', '取消'\]|按钮文字数组
btnColor|Array&lt;String&gt;|\['#FF8E3C', '#999'\]|按钮颜色数组
cb|Array&lt;Function&gt;|-|回调函数数组

示例:
```javascript
app.alert({
    title: '提示',
    content: '弹窗内容',
    btn: ['确定', '取消'],
    btnColor: ['#FF8E3C', '#999'],
    cb: [
        function () {
            app.toast('点击确定');
        },
        function () {
            app.toast('点击取消');
        }
    ]
})
```

## picker(option)
> UIActionSelector选择器模块封装

#### option
字段|类型|默认值|说明
:--:|:--:|:--:|:--:
name|String|-|（可选）选择器命名空间，页面存在多个选择器时充当作用域
data|Array|-|选项数组，元素可为String或Number或{name, value}
active|Number|0|选中项下标（建议用indexOf方式，每次选择就是从当前项开始了）
cb|Function|-|回调函数，回调参数为选择结果{name, value}格式对象

示例:
```javascript
let arr = ['选项1', '选项2', '选项3'];
let val = '选项1';
app.picker({
    name: 'picker_one',
    data: arr,
    active: arr.indexOf(val),
    cb: function (res) {
        val = res.value;
    }
});
```