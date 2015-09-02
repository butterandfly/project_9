### loaders
加载一系列的处理器。对于处理链可能会涉及的文件，都应该有响应的loader。通常涉及的文件包括：
* css文件，包括scss、less等
* 图片文件，jpeg、gif、png、ico
* 矢量文件，svg等
* 字体文件，eot、ttf、woff、svg等
* json

#### API
* 可以直接在require中加载loader
* test是匹配的文件名，exclude则是不包含的

### entry
写成map的形式。

### resolve
提供路径别名等，方便require的使用。

### Webpack-dev-server
服务器，提供socket。

#### historyApiFallback: false
支持html5路由
