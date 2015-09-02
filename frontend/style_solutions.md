## 7个问题

* 全局的命名空间
* 依赖
* 无用代码的去除
* 最小化
* 共享变量
* 无确定性
* 封装

## Scss+Webpack方案

### 7个问题
#### 命名空间、封装与确定性
使用css-loader的"local scope"功能。

#### 用户自定义
使用css-loader后，className会用于封装好的样式；所以要使用role属性让dom可寻。

#### 共享变量与依赖
通过scss的"import"的实现。

#### 最小化
Loader等众多插件可解决。

#### 无用代码的去除
暂无解决方案。

### 缺点
* 组件化后需要处理js、css文件，不如"web component"或CssInJs的只有一个入口

### 优点
* 使用css，便于迁移

### 适用情况
React、无框架项目。

## CssInJs方案

### 变量、重用
* less或scss

### 作用域
* less的selector拼接
* webpack的css-loader的"local scope"

### 可扩展
