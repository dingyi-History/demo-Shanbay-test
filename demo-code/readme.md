## 扇贝小作业 Coding记录

### 2016-01-04 22：10多

> 偶然在QQ邮箱中的广告邮件中看到扇贝的来信小作业，兴奋，加紧要做

* 之前并未做过chrome浏览器插件，原来就是用html、css、js来实现；
* 与前端朋友分享试题，得到一些帮助；
* 《angularjs权威教程》书中第31章 401页，有个教程讲 “构建angularjs Chrome应用”，跟着学一学试试；
* github已有案例参考：
  * https://github.com/wenmine/shanbay_extension
  * https://github.com/Bing573/shanbay-sidekick

#### chrome应用如何工作

* 每个chrome应用都有三个核心文件
* `manifest.json`文件用于描述应用程序的元数据，比如名称、描述、版本以及如何启动这个应用程序；
* 背景脚本：这个背景脚本用于设置应用程序如何响应系统级的事件,比如用户安装你的应用或者启动
它,等等。
* 视图 ： 大多数的Chrome应用程序都有一个视图。这个组成部分是可选的,但是它通常对我们应用
程序而言非常有用。

#### 如何构建自己的chrome应用

* 目录结构

```
+ css/
  - main.css
+ fonts/  
+ js/
  - app.js  //主js文件
  + vendor/
    - angularjs.min.js
- manifest.json
- tab.html
- templates        
```

* manifest.json

```
{
         "manifest_version": 2,
         "name": "Presently",
         "description": "A currently clone",
         "version": "0.1",
         "permissions": ["http://api.wunderground.com/api/"],
         "background": {
             "scripts": ["js/vendor/angular.min.js"]
         },

         // content_security_policy描述应用能做什么不能做什么
         "content_security_policy": "script-src 'self'; object-src 'self'",
         
         //Chrome将应用作为newtab应用启动,设置这个应用覆盖所有新标签页
         "chrome_url_overrides": {
             "newtab": "tab.html"
         }
}

```

* tab.html主页面文件

