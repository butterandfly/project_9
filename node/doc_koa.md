# Doc: Koa
[koajs](koajs.com)

## 基础

### 串联（Cascading）
关于中间件如何串联，可见koajs。

### 设置（Settings）
* `app.name`：应用名字
* `app.env`
* `app.proxy`
* `app.subdomainOffset`

## Middleware
https://github.com/koajs/koa/wiki

* KeyGrip
* mongodb: https://github.com/vdemedes/mongorito

### 路由

#### [koa-router](https://github.com/alexmingoia/koa-router)
路由嵌套：

```javascript
var forums = new Router();
var posts = new Router();

posts.get('/', function *(next) {...});
posts.get('/:pid', function *(next) {...});
forums.use('/forums/:fid/posts', posts.routes());

// responds to "/forums/123/posts" and "/forums/123/posts/123"
app.use(forums.routes());
```

### 模板
可以使用[co-views](https://github.com/tj/co-views)和[koa-views](https://github.com/queckezz/koa-views)。
他们都不自带模板系统，而是与其他模板系统组合使用；你可以选择任何一种：

* [swig](http://paularmstrong.github.io/swig/)
* ext
* [underscore](http://www.css88.com/doc/underscore/)

### Markdown

#### [koa-markdown](https://github.com/koajs/koa-markdown)
