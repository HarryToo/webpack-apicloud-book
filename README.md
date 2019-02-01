# webpack-apicloud
> 放弃jQuery式开发
>> 做不做在我，用不用在你

## 为什么做
- 之前的apiCloud项目开发编码方式过于传统，完全是jQuery + es5，代码不够简练，es6/7很多很好的新特性却不能适用于项目中；
- 之前项目结构陈旧，加上项目的反复迭代变更，使得各个功能封装和模块管理越发显得凌乱；
- 抛砖引玉，我觉得缺的不是多牛多新潮的技术栈，而是每个人都能朝着某个标准、秉着某种细致的态度去开发；
- 也许你有更新更好的技术栈推荐，但至少这也是一种选择。

## 有什么特点
- 开发环境启用HMR，js和样式等依赖文件修改自动热更新，免去每次修改需重新同步再在手机上操作后才能预览效果；
- html统一由html-webpack插件进行模板处理，无需关心html文件头尾部代码和基本静态资源的引用；
- sass预处理器节省样式代码，postcss实现自动补全浏览器兼容样式和px转rem以处理适配问题；
- 引入客户端vue运行环境，方便地随时进行可复用性的vue组件封装，不必每次重复造轮子；
- 使用webpack打包带来环境变量的好处，配置好开发/生产环境接口域名，打包前后不必手动反复切换，减少错漏；
- 为项目带来更好的模块化管理方式、更快捷优雅的es6+编码风格和更多可用的npm依赖。

## 问题及注意
- HMR热更新机制只适用于entry相依赖的文件，只修改html模板无法自更新，针对此问题，在开发环境下页面有提供刷新按钮，尽管如此，同样比真机同步来的快捷；
- 由于src下html属于模板，会交由html-webpack-plugin插件构建处理，其中的img-src地址需采用ejs模板语法，图片也必须当作模块引入，eg：`<img src="<%= require('./img1.png') %>" >`；
- 图片打包构建方式暂一律采用转换为base64，原因是因为开发和生产环境需要的publicPath不一致，而生产环境下安卓设备无法采用如`widget://xx.npg`的绝对路径方式引用图片等资源，好在项目为多页面，同一页面引用图片资源并不多，所以base64方案也影响不大；
- 由于集成的vue为客户端环境版本，开发时请注意自定义组件及prop等名称务必注意单词大小写，eg: `<vue-component :my-prop='true'></vue-component>`。
