## 主要文件目录
```
|-- build                           webpack打包配置文件夹
|   |-- .babelrc                    babel配置文件
|   |-- postcss.config.js           postcss配置文件
|   |-- webpack.common.js           基础构建配置文件
|   |-- webpack.dev.js              开发环境构建配置文件
|   |-- webpack.prod.js             生产环境构建配置文件
|-- dist                            打包输出文件夹
|-- icon                            应用图标（APICloud 本地测试版本使用）
|-- launch                          启动图片（APICloud 本地测试版本使用）
|-- node_modules                    依赖仓库
|-- src                             源码主文件夹
|   |-- assets                      一些需要经过打包构建的封装资源
|   |   |-- app.js                  基于api的一些方法封装
|   |   |-- util.js                 一些工具方法封装
|   |-- components                  vue可复用性组件
|   |-- config                      接口域名和api请求配置
|   |   |-- config.js               开发、生产环境相关接口域名等配置
|   |   |-- req.js                  各种api请求管理配置
|   |-- views                       页面视图文件（html、scss、图片）
|   |   |-- about                   视图模块
|   |   |   |-- about.html                  
|   |   |   |-- about.js                  
|   |   |   |-- about.scss                  
|   |   |   |-- about.png                  
|   |-- index.html                  app入口html
|   |-- index.js                    app入口js
|-- static                          js、css、font等可直接引用的静态资源
|-- .syncignore                     同步忽略配置文件
|-- config.xml
|-- package.json
```

## 整理建议
- `src/assets/app.js` 建议统一存放基于api封装的基本方法，`app`已导出为全局变量，无需反复导入，方便直接通过`app.fun()`方式调用
- `src/assets/util.js` 建议存放业务级别封装方法或者工具方法代码
- `src/components` 建议放置编写的vue组件，可分为基础组件（如按钮、表单等基本元素）、复用性业务模块组件（如某列表功能块）两大类
- `src/views` 存放主要视图模块，建议严格按照模块层级整理目录，用文件夹隔离模块页面各自的html、js、scss及图片，参考上图