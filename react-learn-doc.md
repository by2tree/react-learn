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

Reactk框架的核心优势之一，就是支持创建虚拟DOM**提高页面性能**。

**什么是虚拟DOM?**

​	虚拟 dom 是相对于浏览器所渲染出来的真实 dom 的，在react，vue等技术出现之前，我们要改变页面展示的内容只能通过遍历查询 dom 树的方式找到需要修改的 dom 然后修改样式行为或者结构，来达到更新 ui 的目的。

​	这种方式相当消耗计算资源，因为每次查询 dom 几乎都需要遍历整颗 dom 树，如果建立一个与 dom 树对应的虚拟 dom 对象（ js 对象），以对象嵌套的方式来表示 dom 树，那么每次 dom 的更改就变成了 js 对象的属性的更改，这样一来就能查找 js 对象的属性变化要比查询 dom 树的**性能开销小**。

**为什么操作DOM开销大？**

​	其实并不是查询 dom 树性能开销大而是 dom 树的实现模块和 js 模块是分开的这些跨模块的通讯增加了成本，以及 dom 操作引起的浏览器的回流和重绘，使得性能开销巨大，原本在 pc 端是没有性能问题的，因为 pc 的计算能力强，但是随着移动端的发展，越来越多的网页在智能手机上运行，而手机的性能参差不齐，会有性能问题。

**如何解决性能问题？**

​	angular，react，vue 等框架的出现就是为了解决这个问题的。

​	他们的思想是每次更新 dom 都尽量避免刷新整个页面，而是有针对性的去刷新那被更改的一部分，来释放掉被无效渲染占用的 gpu，cup 性能。

​	**angular** 采用的机制是 脏值检测查机制 所有使用了 ng 指令的 scope data 和 {{}} 语法的 scope data 都会被加入脏检测的队列

​	**vue** 采用的是虚拟 dom 通过重写 setter ， getter 实现观察者监听 data 属性的变化生成新的虚拟 dom 通过 h 函数创建真实 dom 替换掉dom树上对应的旧 dom。

   **react** 也是通过虚拟 dom 和 setState 更改 data 生成新的虚拟 dom 以及 diff 算法来计算和生成需要替换的 dom 做到局部更新的。

```javascript
const HelloWorld = {
    nodeName:'div',
    attrs:{
        className:'',
    },
    css:{
        width: '100px',
        height: '40px',
        color: 'green'
    },
    events:{
        onclick:()=>{ console.log('Hello virtual DOM') }
    },
    childrens:[
        {
            nodeName:'text',
            attrs:{
                innerText:'Hello World',
            },
        }
    ]
}
```

## 1.5 React 渲染机制

1. [React的渲染流程是怎样的？](https://www.jb51.net/article/266712.htm)
2. [React的beginWork都做了什么？](https://www.jb51.net/article/266712.htm#_lab2_1_1)
3. [React的completeWork都做了什么？](https://www.jb51.net/article/266712.htm#_lab2_1_2)
4. React的commitWork都做了什么？
5. useEffect和useLayoutEffect的区别是什么？
6. useEffect和useLayoutEffect的销毁函数和更新回调的调用时机？

# 第2章 React JSX

## 2.1 JSX 介绍

​	JSX其实就是Javascript XML的缩写，JSX作为一种Javascript语法扩展，支持自定义属性，并具有很强的扩展性。JSX是React框架内置的语法。

​	React项目中使用 JSX语法，则必须引用“bable.js”来解析JSX。“ script type="text/babel" ”

## 2.2 JSX 独立文件

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script type="text/babel">
    const reactSpan = (
         <span>
            <h3>react JSX</h3>
            <p>creat react dom by react jsx.</p>
         </span>
    )
    ReactDOM.render(
        reactSpan,
        document.getElementById("root")
    )
</script>

</html>
```

## 2.3 JSX 表达式

​	React JSX 使用的就是 JavaScript 语法，那么自然可以使用JavaScript表达式。在React JSX 使用JavaScript表达式使用 大括号 **{}** 括起来。

​	React JSX 中的 JavaScript 表达式有很多种：**条件表达式**、**嵌入表达式**、**对象表达式**、**函数表达式**、**增强函数表达式**、**数组表达式**、**样式表达式**、**注释表达式**。

### 2.3.1 JSX 算术表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
    const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>8+8 = { 8 + 8 }</p>
         </span>
    )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.2 JSX 条件表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
    const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p> test exp “ 1 = 1 ” { 1 == 1 ?  "true" : "false" }</p>
            <p> test exp “ 1 != 1 ” { 1 != 1 ? "true" : "false" }</p>
         </span>
    )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.3 JSX 嵌入表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
  const name = "Tom"
    const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>{name}</p>
         </span>
    )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.4 JSX 对象表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
  const userInfo = {
      name:"Tom",
      sex: "男",
      age:20
  }
    const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>用户信息 {'>>'} 名字：{userInfo.name}，性别：{userInfo.sex}，年龄：{userInfo.age}</p>
         </span>
    )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.5 JSX 函数表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
  const userInfo = {
      name:"Tom",
      sex: "男",
      age:20
  }

  function formatUserInfo(userInfo) {
    return "名字：" + userInfo.name +"，性别："+userInfo.sex +"，年龄："+userInfo.age
  }
  
  const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>用户信息 {'>>'} {formatUserInfo(userInfo)}</p>
         </span>
   )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.6 JSX 增强函数表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>


<script  type="text/babel">
  const room = document.getElementById("root")
  const userInfo = {
      name:"Tom",
      sex: "男",
      age:20
  }

  function formatUserInfo(userInfo) {
      if(userInfo) {
         return "名字：" + userInfo.name +"，性别："+userInfo.sex +"，年龄："+userInfo.age
      } else {
         return "userInfo is nothing."
      }
  }
  
  const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>用户信息 {'>>'} {formatUserInfo(userInfo)}</p>
            <p>用户信息 {'>>'} {formatUserInfo()}</p>
         </span>
   )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.7 JSX 数组表达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")
  
  const arrayUserInfo = [
    <span>name:tom,</span>,
    <span>男,</span>,
    <span>20</span>
  ]
  
  const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p>{arrayUserInfo}</p>
         </span>
   )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.8 JSX 样式达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")

  const css_p_lg = {
    fontSize:20,
    color:"red"
  }

  const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p style={css_p_lg}> react JSX Style Expression</p>
         </span>
   )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

### 2.3.9 JSX 注释达式

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script  type="text/babel">
  const room = document.getElementById("root")

  const css_p_lg = {
    fontSize:20,
    color:"red"
  }
  const reactSpan = (
         <span>
            <h3>react JSX Expression </h3>
            <p style={css_p_lg}> react JSX Style Expression</p>
            {/* 注释 （界面不显示） */}
            /* 注释 （界面显示） */
         </span>
   )
    ReactDOM.render(
        reactSpan,
        room
    )
</script>

</html>
```

# 第3章 React 组件与Props

## 3.1 React 组件

​	React组件可以将UI切分成独立的，可复用的部件。React 组价从形式上看很像是JavaScript函数，通过这个函数返回一个需要页面上展示的React元素。

​	React语法是基于版本ECMScript 6 实现的，因此，React组件除了通过JavaScript·函数的形式，还可以通过ES6 Class(类)的形式来实现。

> **React组件的名称首字母必须是大写** 。
>
> 首字母不大写报错：unrecognized in this browser. If you meant to render a React component, start its name with an uppercase letter.
>
> 这个规定主要是为了与原生的html标签名称相区别。

​	**函数：**

```javascript
function reactComponent() {
    return <p> hello ,react component.</p>
}
```

​    **类：**

```javascript
class reactComponent extends React.Component {
    render() {
        return <p> hello ,react component. </p>
    }
}
```

### 3.1.1 React 函数组件

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>

<script type="text/babel">
   const root =  document.getElementById("root")
   // 函数首字母必须是大写！
   function HelloReactComponent(){
      return <p> hello ,react component. </p>
   }

   const elHello = <HelloReactComponent/>
   // React JSX
   const reactSpan = (
         <span>
            <h3>React 函数组件</h3>
           {elHello}
         </span>
    )
    ReactDOM.render(
      reactSpan,
      root
    )
</script>

</html>
```

### 3.1.2 React 类组价

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>


<script type="text/babel">
   const root =  document.getElementById("root")
   // class Component （ 首字母必须是大写！）
   class HelloReactComponent extends React.Component {
      render(){
         return <p> hello ,react component. </p>
      }
   }
   const elHello = <HelloReactComponent/>
    // React JSX
    const reactSpan = (
         <span>
            <h3>React 类组件</h3>
           {elHello}
         </span>
    )
    ReactDOM.render(
      reactSpan,
      root
    )
</script>

</html>
```

### 3.1.3 React 组合组件

```javascript
<html>
 <head>
    <script src="https://unpkg.com/react@16/umd/react.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"  crossorigin ></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"   ></script>
 </head>

<body>
   <div id="root"></div>
</body>


<script type="text/babel">
   const root =  document.getElementById("root")

   function FormTitle(){
      return <h4> User Login </h4>
   }

   function UserName() {
      const userName = (
         <p>username：<input type="text"/></p>
      )
      return userName
   }

   function Password(){
      const passwd = (
         <p>password：<input type="password"/></p>
      )
      return passwd
   }

   function Submit(){
      const submit = (
         <p><button> login </button></p>
      )
      return submit
   }

   function FormLogin() {
      return (
         <>
            <FormTitle/>
            <UserName/>
            <Password/>
            <Submit/>
         </>
      )
   }
 
   const reactSpan = (
      <span>
         <h3>React 组合组件</h3>
        {<FormLogin/>}
      </span>
   )
    ReactDOM.render(
      reactSpan,
      root
    )
</script>

</html>
```









