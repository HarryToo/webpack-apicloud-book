## 主要文件目录
```
|-- webpack-apicloud
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
    |   |-- assets                      一些需要经过打包的封装工具包
    |   |   |-- app.js                  基于api的一些方法封装
    |   |   |-- util.js                 一些工具方法封装
    |   |-- components                  vue可复用性组件（可分为基础组件、复用性模块组件）
    |   |-- config                      接口域名和api请求配置
    |   |   |-- config.js               开发、生产环境相关接口域名等配置
    |   |   |-- req.js                  各种api请求管理配置
    |   |-- views                       页面视图文件（html、scss、图片）
    |   |   |-- about                   建议严格模块层级整理目录
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

## 建议
- 1234