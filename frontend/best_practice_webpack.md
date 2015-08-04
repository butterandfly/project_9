# Webpack实战

### 参考资料
http://segmentfault.com/blog/jiyinyiyong/1190000002552008
http://segmentfault.com/blog/jiyinyiyong/1190000002551952

### 自定义模块路径
```javascript
root: [path.join(__dirname, "bower_components"), path.join(__dirname, 'app_components')]
```

### 使用bower

```javascript
var path = require("path");
var webpack = require("webpack");

module.exports = {
  resolve: {
    root: [path.join(__dirname, "bower_components"), path.join(__dirname, 'app_components')]
  },
  plugins: [
    new webpack.ResolverPlugin(
      new webpack.ResolverPlugin.DirectoryDescriptionFilePlugin("bower.json", ["main"])
    )
  ]
}
```

### require时直接使用全局（window）变量

```javascript
externals: [
  "moment"
],
```