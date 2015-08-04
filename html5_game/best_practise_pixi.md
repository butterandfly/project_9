# 实战：Pixi

## Beginning
创建舞台(stage)，这是显示的根：
```
var stage = new PIXI.Stage(0xffffff);
```

创建renderer:
```
// 浏览器支持webgl的情况会得到WebglRenderer，否则得到CanvasRenderer
var renderer = PIXI.autoDetectRenderer(400, 300);
```

开始：
```
    requestAnimFrame( animate );
        function animate() {
	        requestAnimFrame( animate );
		        renderer.render(stage);
			    }
			    ```

## Renderer
属性：
```
renderer.width;
renderer.height;
```

## 加载资源
注意用TexturePacker生成sheet的时候图片的长宽要设置为2的倍数，不然会报错。
```
// create an array of assets to load
var assetsToLoader = [ "SpriteSheet.json"];

// 创建一个新的loader
loader = new PIXI.AssetLoader(assetsToLoader);

// 加载每一项的回调
loader.onProgress = function() {
  // dealing
  }

// 全部资源都加载成功时：
loader.onComplete = onAssetsLoaded

//begin load
loader.load();
```

## 创建精灵
```
// 加载图片
var texture = PIXI.Texture.fromImage("bunny.png");
// 通过图片创建精灵
var bunny = new PIXI.Sprite(texture);

// 设置锚点
bunny.anchor.x = 0.5;
bunny.anchor.y = 0.5;

// 设置位置
bunny.position.x = 200;
bunny.position.y = 150;

// 把精灵添加到舞台中
stage.addChild(bunny);
```

## 几何图案
```
    // 画一个方形
        var g = new PIXI.Graphics();
	    g.lineStyle(5);
	        g.beginFill(0xffffff, 1.0);
		    g.drawRect(0, 0, 100, 100);
		        // 默认会有padding，通过设置将padding消去
			    g.boundsPadding = 0;
			    ```

同时我们可以通过graphic来生成texture创建sprite或tilingSprite
```
var sprite = new PIXI.Sprite(g.generateTexture());
var tilingSprite = new PIXI.TilingSprite(g.generateTexture(), 1000, 1000);
```

## 动画
```
var animation = new PIXI.MovieClip(textureArray);
```

## 输入
### 启用sprite的交互
```
sprite.interactive = true;
sprite.hitArea = new PIXI.Rectangle(0, 0, 100, 100);
```
### 点击
```
stage.mousedown = stage.touchstart = function(e) {
  // 点击坐标
    e.global.x;
      e.global.y;
      }
      ```

### 鼠标/触摸移动
```
stage.mousemove = stage.touchmove = function(e) {
  // 该坐标是相对父object的位置
    e.global.x;
      e.global.y;
      }
      ```

## 关于anchor与pivot
`anchor`属性计算百分比，`pivot`则是实际像数。DisplayObjectContainer（或者是已经addChild的sprite）中没有anchor属性，可以用pivot代替。
另外DisplayObjectContainer现在是不能修改width和height的，不知道是bug还是设计本意。