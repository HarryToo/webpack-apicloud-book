# 使用

## 前置
1. [Node.js](http://nodejs.cn)环境、npm/[cnpm](http://npm.taobao.org)
2. （可选）安装[apicloud-cli](https://www.npmjs.com/package/apicloud-cli) —— apicloud官方提供的基于node的wifi同步命令工具

## 步骤
1. 执行`npm i`安装项目基础依赖
2. 修改`config.xml`的入口html地址
```xml
<!--开发环境为http://本机IP:8888/index.html-->
<content src="http://192.168.1.2:8888/index.html"/>
```
3. 执行`npm run server`启动开发环境服务，首次需wifi同步一次
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
- 启动开发环境服务时，请务必确保对`config.xml`中入口文件地址作了对应的修改，另外**`openWin`等方法的url确保都使用了[`app.resolvePath()`](/doc/app.html#resolvepathurl)方式解析**
- 由于src下html属于模板，会交由html-webpack-plugin插件构建处理，其中的img-src地址需采用ejs模板语法，图片也必须当作模块引入，eg：`<img src="<%= require('./img1.png') %>" >`，小于10kb的图片在生产构建后将转为Base64形式引用
- 由于集成的vue为客户端版本即dom模板环境，使用自定义组件及prop等时候务必遵守[`kebab-case`命名规范](https://cn.vuejs.org/v2/style-guide/#%E6%A8%A1%E6%9D%BF%E4%B8%AD%E7%9A%84%E7%BB%84%E4%BB%B6%E5%90%8D%E5%A4%A7%E5%B0%8F%E5%86%99-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)，eg：`<vue-component :my-prop='true'></vue-component>`