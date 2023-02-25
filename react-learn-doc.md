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

## 1.3 React 虚拟DOM



## 1.4 React 渲染机制



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









