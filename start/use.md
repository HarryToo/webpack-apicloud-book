## 步骤
1. （可选）安装apicloud-cli —— apicloud官方提供的基于node的wifi同步命令工具
```
npm i apicloud-cli -g
```
2. 安装项目基础依赖
```
npm i
```
3. 修改`config.xml`的入口html地址
```xml
<!--开发环境为本机IP-->
<content src="http://192.168.1.2:8888/index.html"/>
```
4. 执行`npm run server`启动开发环境服务，wifi同步一次
5. 愉快的 coding 阶段 😑...
6. 修改`config.xml`的入口html地址
```xml
<!--生产环境为dist目录-->
<content src="dist/index.html"/>
```
7. 执行`npm run build`开始生产环境打包构建

## NPM scripts
命令|说明
:--:|:--:
wifiStart|启动wifi同步服务
wifiStop|关闭wifi同步服务
wifiLog|启动wifi日志服务
update|wifi增量同步
updateAll|wifi全量同步
server|启动本地开发环境服务
build|生产打包构建