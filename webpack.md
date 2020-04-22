####解决的痛点问题
#####模块化
- 模块直接在全局工作，大量模块成员污染全局作用域；
- 没有私有空间，所有模块内的成员都可以在模块外部被访问或者修改；
- 一旦模块增多，容易产生命名冲突；无法管理模块与模块之间的依赖关系；
- 在维护的过程中也难分别成员属性
#####命名空间
window.ns_01={}
window.ns_02={}
####IIFE(Immediately-Invoked Function Expression)立即执行函数表达式
(function(){})() 引入私有成员概念
####IIFE 依赖参数
(function($){})(JQuery)
#####解决
- 模块加载
- 代码组织
- 维护代价
- 与html耦合

####规范化出现
##### CommonJS
Node.js 遵循的规范，该规范约定，一个文件就是一个模块，每个模块都有单独的作用域，通过 module.exports 导出成员，再通过 require 函数载入模块。同步加载方式，浏览器模式下性能下降。
##### AMD(Asynchronous Module Definition)
 异步模块规范，require.js
在AMD规范中约定每个模块通过define()函数定义，这个函数默认可以接收两个参数，第一个参数是一个数组，用于声明此模块的依赖项；第二个参数是一个函数，参数与前面的依赖项一一对应，每一项分别对应依赖项模块的导出成员，这个函数的作用就是为当前模块提供一个私有空间。如果在当前模块中需要向外部导出成员，可以通过 return 的方式实现。
使用复杂，同一个页面对 js 文件的请求次数过多的情况，从而导致效率降低
#####ES Module
import {foo} from './module/foo.js'

####webpack解决的问题
支持不同类型的前端模块。css png 等
散落相同的模块组合一起，降低浏览器频繁请求模块文件
具备代码编译能力，兼容大多数的环境


###Sample
type="module" 这种用法是 ES Modules 中提出的标准，用来区分加载的是一个普通 JS 脚本还是一个模块。

npm init --yes 
npm install webpack webpack-cli --save-dev
npx webpack --version
npx 是 npm 5.2 以后新增的一个命令，可以用来更方便的执行远程模块或者项目 node_modules 中的 CLI 程序

###webpack.config.js
webpack.config.js 是一个运行在 Node.js 环境中的 JS 文件，也就是说我们需要按照 CommonJS 的方式编写代码，这个文件可以导出一个对象
```javascript
const path = require('path')
module.exports={
	entry:'./src/main.js',
	output:{
		filename:'bundle.js',
    	path: path.join(__dirname, 'output')
    }
}
```
#### webpack loader
npm install css-loader --save-dev
or yarn add css-loader --dev
修改配置如下
```javascript
module.exports={
	entry:'./src/main.css',
	output:{filename:'bundle.js'},
	module:{
		rules:[
		{
			test:/\.css$/,//根据打包过程中所遇到文件路径匹配是否使用这个loader
			use: [
			  'style-loader',//在 css-loader 的基础上再使用一个 
			                 //style-loader，把 css-loader 
			                 // 转换后的结果通过 style 标签追加到页面上
			  'css-loader'// 指定具体的 loader
			  ]
      	}]
     }
}
```
#### 自定义loader
















