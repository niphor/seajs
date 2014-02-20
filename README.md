A Fork Of Seajs with Non-CMD Module Shim Build-in
===

Sea.js is a module loader for the web. It is designed to change the way that you
organize JavaScript. With Sea.js, it is pleasure to build scalable web applications.

The official site: <http://seajs.org/>

## 原因

记得看Issus时有个大大说过，Seajs的玩法就是自己fork一份自己玩。

鉴于Seajs社区是朝着CMD规范靠拢的，而我等懒货在开发时绝壁不想该上游库包的，所以fork一份把原先的Shim补回来了...

## 为什么不弄成插件

Seajs 2.0.x可以把Shim做成插件的原因是内部模块加载方式导致的

2.1.x要支持只能改动内部代码，支持对Non-CMD模块的延迟加载

改动虽然不大，但是再搞成插件形式意义好像不大了，才30行代码...

## 使用
所有Non-CMD模块加载前必须在Config里按照之前Shim插件的形式添加别名

```js
seajs.config({
 alias: {
   "jquery": {
     src: "lib/jquery.js",
     exports: "jQuery" or function
   },
   "jquery.easing": {
     src: "lib/jquery.easing.js",
     deps: ["jquery"]
   }
 })
```


## 注意事项

+ 没加别名一律当做CMD模块加载
+ 没有添加循环依赖判断
+ 生产环境谨慎使用