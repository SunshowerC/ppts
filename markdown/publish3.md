title: vue 前端开发
speaker: willchen
url: https://github.com/chenweiyu/ppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: moon
usemathjax: yes

[slide data-transition="vertical3d" style="background-image:url('./img/timg.jpg');background-size: 100% 100%;"]
# 发布系统前端技术分享

[slide data-transition="vertical3d"]
# 大纲
* 前端工程化
 * 为什么需要工程化    
 * 工程化演进过程
 * 通过webpack实现前端工程化

* 单页面应用（SPA）
 * 传统开发方式介绍 
 	* SSR（Server-Side-Render）
 	* jQuery  
 * SPA 开发方式介绍
 * SPA 优缺点
 * SPA 适用场景

* SPA框架：Vue
 * Vue 介绍
 * Vue原理解析 (MVVM + Vistual DOM)
 * jQuery 和 Vue 业务实现对比
 * Vue 性能对比
 * Vue 构建应用及其生态
 






[slide data-transition="vertical3d"]
# 为什么需要工程化
随着前端技术的发展，搭建复杂的前端应用不再是简单的html + css + html，而是需要做到更多: 

模块化依赖管理，es6 babel编译器，css预编译，

代码合并，代码压缩，代码混淆加密，图片压缩，文件缓存管理，热加载
 lint代码检查，mock模拟数据，单元测试，UI自动化测试。

* 开发效率：代码规范，javascript编译，css预处理，模块化管理，数据 mock，热加载...
* 性能优化：
    图片压缩，代码压缩，代码合并，文件缓存管理
* 代码复用：
    web组件化
这些统称为前端工程化，或者是前端构建自动化







[slide data-transition="vertical3d"]
# 演进过程

* `<script>`混乱加载
* 各种模块化系统标准：commonjs/amd/es6 module
* 模块化加载器：requirejs/seajs/systemjs
* 自动化构建工具：grunt，gulp
* 模块化打包器：webpack/r.js/jspm/browserify
 * 合并入口，对外只暴露entry point
 * 提供浏览器运行环境（内置模块加载器）
 * 优化（代码压缩，混淆加密，tree-shaking无用代码移除）



[slide data-transition="vertical3d"]
# 通过webpack实现前端工程化
* npm（node package manager） 包管理器
<img src="./img/node.jpg" alt="node">
<img src="./img/npm.jpg" alt="npm">
<img src="./img/webpack.jpg" alt="webpack">
<img src="./img/es6.jpg" alt="es6">
<img src="./img/babel.jpg" alt="babel">












[slide data-transition="vertical3d"]
# 单页面应用（SPA）


[slide data-transition="vertical3d"]
# 传统开发方式（服务端渲染）
	* 前后端耦合
	* 前后端沟通成本高

<!-- 后端模板引擎，渲染生成HTML之后，返回给浏览器  
以后端为主的 MVC 架构方式。具体来说，每次项目评审后，前后端会先一起约定好接口，之后分别进行开发。通常前端会在本地先写好Demo并跑通前端逻辑，之后再将html文件交给后端开发套ftl模板。正式基于这样的开发模式，导致了总工作量的增加，同时沟通和联调成本的消耗也十分显著。-->





[slide data-transition="vertical3d"]
# SPA 开发方式
1. 单个页面（只有一个HTML文件）
2. 前端路由
3. 数据交互全部通过 ajax 进行



[slide data-transition="vertical3d"]
# SPA 优缺点
* 特点：
	* 后端服务化。良好的前后端分离，前端负责界面显示，后端负责数据存储和计算，不再负责模板渲染、输出页面工作。
	* 减轻服务器压力。服务器只用出数据就可以，不用管展示逻辑和页面合成，提高服务器吞吐能力。
	* 用户体验好、快，内容的改变不需要重新加载整个页面。

* 缺点：
	* 不利于SEO。
<!-- 当然，解决这个SEO的方法不是没有，各大框架的开发团队也有提供具体的SEO解决方案，但这毫无疑问增加的开发成本，所以市面上，商业网站使用前端框架的比较少  -->


[slide data-transition="vertical3d"]
# SPA 适用场景
适用：
1. 内部网站
2. 用户个人信息页面
3. 所有不需要SEO的web应用
<!-- 购物车，知乎live 就是用react 做成的一个SPA -->

不适用：
1. 商业网站，重SEO，重首屏加载体验。
2. 业务简单，变动可能较小，页面数少的web应用。



[slide data-transition="vertical3d"]
# 怎么实现一个SPA
jQuery ?

[slide data-transition="vertical3d"]
# jQuery 时代
<img src="./img/gan.png" alt="">
jQuery的出现给早期的前端领域注入了一剂强心剂，前端工程狮们不再需要投入大量的精力去解决那些令人蛋疼的浏览器兼容问题，从而减少了项目跨浏览器兼容的工作量。
<!-- jquery 2006 ; es5 2009 ; es6 2015; es8 2017 -->
<!-- jQuery的劣势也非常明显，因为需要各种兼容所以代码显得特别重 -->





<!-- 另外就是全DOM操作，钩子往往会依赖标签，如果依赖jQuery来搭建页面的话（比如后台输出json，然后jQuery loop一个列表出来），维护上会有困难。如果一改页面结构，很多依赖标签的选择器，一改起来js那块就得跟着大改，代码维护成本高。随着业务复杂度的增加、jQuery写起来的项目复杂度是指数级增加的。
频繁操作dom 元素，性能问题。
 -->
而vue、react、ng等框架可以一定程度的抽象、再加上webpack、对于后面的维护、还有业务代码的扩展性是很方便的


[slide data-transition="vertical3d"]
# SPA框架：Vue
其和jQuery最大的不同点在于jQuery通过操作DOM来改变页面的显示，而Vue通过操作数据来实现页面的更新与展示。

jQuery是MVC开发模式的一个代表。在jQuery代码中，controller中存在大量的和view耦合的逻辑，例如jq中的html片段拼接，无法复用和维护困难。

Vue是基于MVVM开发模式的框架。相比于MVC，我认为MVVM在处理UI交互方面应该是抽象的最全面的模式。





[slide data-transition="vertical3d"]
# Vue 介绍
数据驱动

当View层的视图发生改变时，Vue会通过DOM Listeners来监听并改变Model层的数据。相反，当Model层的数据发生改变时，其也会通过Data Bingings来监听并改变View层的展示。这样便实现了一个双向数据绑定的功能，也是Vue.js数据驱动的原理所在。




[slide data-transition="vertical3d"]
# jQuery 和 Vue 业务实现对比
1. 便捷（table 比较）
2. 高度可复用（新建，修改页面 复用一套）

低耦合、可复用、可测试、易维护。
```
// jQuery
data.forEach(function(item){
    $(ul).append(`
    <li class="...">
    ...
        <a class="...">
           item.value
        </a>
    ...
    </li>
    `);
})

// vue
<template>
   <ul-component :data="ulList"></ul-component>   
</template>
<script>
    ...
    this.ulList = data;
    ...
</script>




```

[slide data-transition="vertical3d"]
# Vue原理解析 (MVVM + Vistual DOM)

<img src="./img/vue.jpg" alt="">



[slide data-transition="vertical3d"]
# Vue 性能对比
* angular (脏检查)
* vue (数据劫持)
* react (View层)
// 第三方跑分比较

[slide data-transition="vertical3d"]
# Vue 构建应用及其生态
1. 模块化组件化
将业务组件抽离成`.vue`文件，便于维护，避免css样式污染，
2. 前端路由（vue-router）
3. 数据交互通信（axios）
4. 状态管理器（vuex）
5. UI组件库
ElementUI, MintUI(移动端)，iView ...


















 



 
    



 

 

 





