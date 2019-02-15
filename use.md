# 使用

## 前置
1. [Node.js](http://nodejs.cn)环境、npm/[cnpm](http://npm.taobao.org)
2. （可选）安装[apicloud-cli](https://www.npmjs.com/package/apicloud-cli) —— apicloud官方提供的基于node的wifi同步命令工具

## 步骤
1. 安装项目基础依赖
```
npm i
```
2. 修改`config.xml`的入口html地址
```xml
<!--开发环境为本机IP-->
<content src="http://192.168.1.2:8888/index.html"/>
```
3. 执行`npm run server`启动开发环境服务，wifi同步一次
4. 愉快的 coding 阶段 😑...
5. 执行`npm run build`开始生产环境打包构建
6. 拿到`dist`目录下文件去APICloud平台进行应用打包

## NPM scripts
script|说明
:--:|:--:
wifiStart|启动wifi同步服务
wifiStop|关闭wifi同步服务
wifiLog|启动wifi日志服务
update|wifi增量同步
updateAll|wifi全量同步
server|启动本地开发环境服务
build|生产打包构建

## 注意
- HMR热更新机制只适用于entry相依赖的文件，修改html模板和static文件夹下静态资源无法触发自更新，针对此问题，在开发环境下页面有提供刷新按钮，尽管如此，同样比真机同步来的快捷
- 启动开发环境服务或者执行生产环境构建时，请务必确保对`config.xml`中入口文件地址作了对应的修改，另外**`openWin`方法的url确保都使用了`app.resolvePath()`[^①] 方式解析**
- 由于src下html属于模板，会交由html-webpack-plugin插件构建处理，其中的img-src地址需采用ejs模板语法，图片也必须当作模块引入，eg：`<img src="<%= require('./img1.png') %>" >`
- 图片打包构建方式暂一律采用转换为base64，原因是开发和生产环境需要的publicPath不一致，而生产环境下安卓设备无法采用如`widget://xx.npg`的绝对路径方式引用图片等资源，好在项目为多页面，同一页面引用图片资源并不多，所以此方式也影响不大
- 由于集成的vue为客户端环境版本，开发时务必注意使用的自定义组件及prop等名称单词的大小写，eg: `<vue-component :my-prop='true'></vue-component>`

---
[^①]: `app.resolvePath()` 方法维持页面在server或build环境下的跳转关联