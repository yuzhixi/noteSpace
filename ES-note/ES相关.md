### ES6模块化使用，开发环境打包
**基本语法**

> export 导出，可以导出多个对象，import 导入：import { fn1,fn2}
> export default 导出一个基本对象 , import 导入基本对象： import fn

**开发环境配置**

 _babel_：让浏览器支持es6语法

>  node环境
>  npm安装babel


**JS众多模块化标准**

_1,webpack_

> 配置webpack.config.js
> 配置package.json中的script:start
> 运行npm start

_2,rollup_

> vue、react均用rollup打包
> rollup功能单一，学习成本低，webpack功能强大，学习成本高
_工具设计要尽量功能单一，可集成，可扩展_

### class和构造函数的区别

> class在语法上更加贴合面向对象的写法
> class实现继承更加易读、易理解
> 更易于java等后端语言的使用
> 本质还是语法糖，使用prototype
### Promise的基本使用和原理
#### 基本用法
> new Promise实例，并return
> 
> new Promise 时传入函数，函数参数为resolve，reject。成功时执行resolve(),失败时执行reject()
> 
> then监听结果


```JavaScript
const promise = new Promise(function(resolve, reject) {
  // ... some code
  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});

promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```
#### 封装使用
```JavaScript
function loadImg(src){
    const promise = new Promise(function(resolve, reject) {
      // ... some code
      var img = document.createElement('img')
      img.onload = function () {
        resolve(img);
      } else {
        reject();
      }
      img.src = src
    })
    return promise
}

var result = loadImg('src')
result.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

## ES6的其他常用功能

> 1. let定义变量，const定义常亮
> 1. 多行字符串/模板字符串：`` / ${}
> 1. 解构赋值
> 1. 块级作用域
> 1. 函数默认参数
> 1. 箭头函数

### ES6的其他常用功能
