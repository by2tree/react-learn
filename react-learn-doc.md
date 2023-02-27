# 第1章 React 简介

## 1.1 React 概述

​	React是一个用于构建用户页面的js库，专注于视图，实现组件化开发。主要用来写HTML页面或者构建Web应用，起源于Facebook内部项目，可以进行安卓、ios移动端开发，使用虚拟**Dom**和**Diffing**算法，尽量减少与真实dom的交互提高性能。

**React 框架的主要优点：**

- 声明式设计：React采用声明范式，可以轻松描述应用。
- ​        高  效：React通过DOM的模拟，最大限度地减少与DOM的交互。
- ​        灵  活：React可以与已知的库或框架很好地配合。
-    JSX语法：JSX是JavsScript语法的扩展，可以极大提高JS运行效率。
-   组件复用：通过React构建组件使得代码易于复用，可在大型项目应用开发发挥优势。
- 单向响应的数据流：React实现了单向响应的数据流，减少了重复代码，比传统的数据绑定方式**更简单**。

## 1.2 第一个React应用

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js" crossorigin ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script type="text/babel">
    ReactDOM.render(
        <h1>hello word!</h1>,
        document.getElementById("root")
    )
</script>

</html>
```

## 1.3 React 脚手架

​	Web前端应用几乎都拥有非常复杂的项目架构。React项目开发也是如此，比较流行的做法是采用Webpack+ES6的模式来搭建项目架构，然后通过打包方式发布Web应用。

​	 涉及React项目开发的技术点有很多，比如：Nodejs，npm包管理工具、webpack模块打包器、ES6（[ECMAScript6](https://es6.ruanyifeng.com/)），以及Bable [ˈbeɪbl] 编译器等。<img src="https://es6.ruanyifeng.com/images/cover-3rd.jpg" alt="img" style="zoom:25%;" />

```html
ECMA  欧洲计算机制造商协会(European Computer Manufacturers Association)
```

​	React脚手架产品有很多，不过最著名的还是Fecebook自己推出的 **creat-react-app**脚手架。1.4 React 虚拟DOM

​	Node.js 是 JavaScript 的服务器运行环境（runtime）。它对 ES6 的支持度更高。除了那些默认打开的功能，还有一些语法功能已经实现了，但是默认没有打开。使用下面的命令，可以查看 Node.js 默认没有打开的 ES6 实验性语法。

```shell
// Linux & Mac
$ node --v8-options | grep harmony

// Windows
$ node --v8-options | findstr harmony
```

 **Bable转码器**

​	[Babel](https://babeljs.io/) 是一个广泛使用的 ES6 转码器，可以将 ES6 代码转为 ES5 代码，从而在老版本的浏览器执行。这意味着，你可以用 ES6 的方式编写程序，又不用担心现有环境是否支持。下面是一个例子。

>  npm install --save-dev @babel/core

```javascript
// 转码前
input.map(item => item + 1);

// 转码后
input.map(function (item) {
  return item + 1;
});
```

**实例：create-react-app脚手架创建应用**

- 安装create-react-app脚手架

```shell
npm install -g create-react-app                    // 全局安装

npm install  create-react-app   
```

- 创建应用

```shell
npx create-react-app learn_1.3
```

- 启动应用

```shell
 npm start
 
 http://localhost:3000/      //浏览器访问
```

## 1.4 React 虚拟DOM



## 1.5 React 渲染机制



# 第2章 React JSX

## 2.1 JSX 介绍

## 2.2 JSX 独立文件

## 2.3 JSX 表达式

### 2.3.1 JSX 算术表达式

### 2.3.2 JSX 条件表达式

### 2.3.3 JSX 嵌入表达式

### 2.3.4 JSX 对象表达式

### 2.3.5 JSX 函数表达式

### 2.3.6 JSX 增强函数表达式

### 2.3.7 JSX 数组表达式

### 2.3.8 JSX 样式达式

### 2.3.9 JSX 注释达式



# 第3章 React 组件与Props









