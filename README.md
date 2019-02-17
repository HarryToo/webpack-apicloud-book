# webpack-apicloud
> 放弃jQuery式开发，方便一点、清晰一点

## 为什么做
- 之前项目前端交互方式主要依靠jQuery，逻辑状态复杂时dom操作反复繁琐，维护不便
- 之前项目编码风格完全基于es5，代码冗长不够简练，眼看es6+很多很好的新特性却不能适用于项目中
- 之前项目结构陈旧，加上项目的反复迭代变更，仅有的`common.js`在各种花样填充下，各个功能封装和代码复用方式越发显得凌乱
- 之前项目开发阶段真机调试略显麻烦，每次改动页面样式或js代码，需要重新同步后再重新操作跳转至当前页面才能观察效果
- 抛砖引玉，个人觉得重要的不是多牛多新潮的技术栈，而是都能朝着某个标准、秉着某种细致的开发态度去做
- 也当作是个人练习，也许你有更新更好的技术栈推荐，但至少这也是一种不贵的选择，做不做在我，用不用在你

## 做了什么
- 根据实际开发情况，在APICloud项目基础上，加入基本的[webpack](https://webpack.docschina.org/concepts)构建方式，动态entry，各环境的配置及相关模块的解析处理
- 对于js，使用[Babel](https://babel.docschina.org)+[Polyfill](https://babel.docschina.org/docs/en/babel-polyfill)编译；对于样式编写及适配，引入[Sass](https://www.sass.hk)及[Postcss](https://www.postcss.com.cn)处理器
- 放弃jQuery，各方面考量下选择了引用客户端环境的[Vue.js](https://cn.vuejs.org/v2/guide)，处理了方法及Vue实例等变量导出及使用方式
- 个别问题的试探和处理，如点击延时、Vue中`tapmode`使用方案、图片文件打包构建和压缩、资源引用路径和方式、文件和项目基本结构设计等
- 参照以往项目情况，完成了一些基本的变量、方法、组件和指令的封装，各环境配置构建及优化整理，demo编写及测试

## 有什么用
- 开发环境启用[HMR](https://webpack.docschina.org/concepts/hot-module-replacement)，js和样式等依赖文件修改自动热更新，免去每次修改需重新同步再在手机上操作后才能预览效果
- html统一由[HtmlWebpackPlugin](https://webpack.docschina.org/plugins/html-webpack-plugin)进行模板处理，无需关心html文件头尾部代码和基本静态资源的引用
- Sass预处理器节省样式代码，Postcss实现自动补全浏览器兼容样式和px转rem以处理适配问题
- 生产构建时会将小于10kb的图片文件转为Base64形式直接引用，其余图片会进行适当的压缩处理，以减少项目体积，
- Vue.js代替jQuery来处理交互及模板渲染更加友好，其组件特性和模块化也更方便地随时进行可复用性的vue组件封装，不必每次重复造轮子
- 使用webpack打包带来环境变量的优点，配置好开发/生产环境接口域名，打包前后不必手动反复切换，减少出错
- 为项目带来更好的模块化管理方式、更快捷优雅的es6+编码风格和更多可用的npm依赖
