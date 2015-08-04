# 实战：Phaser

## 创建一个游戏
```
var game = new Phaser.Game(800, 600, Phaser.CANVAS, 'phaser-example', { preload: preload, create: create, update: update });
```

其中加载的内容都放在preload内，例如：
```
function preload() {
    game.load.image('sky', 'assets/skies/sunset.png');
    }
    ```

初始化的内容放在create：
```
function create() {
    game.add.image(0, 0, 'sky');
        // and so on...
	}
	```

## 加载资源
```
// 加载边界
game.load.physics('physicsData', './sprites.json');

// 加载sheet
game.load.spritesheet('chain', './chain.png', 16, 26);
```

## 基本设置
```
// 背景色
game.stage.backgroundColor = '#eeeeee';

// 游戏边界
game.world.setBounds(0, 0, 1920, 1000);
```

## Sprite
### z轴
```
// 将sprite的显示放在最上层
sprite.bringToTop()
```

## 使用p2

### 设置
首先你得开启物理引擎：
```
game.physics.startSystem(Phaser.Physics.P2JS);
```

然后你可以对物理引擎做一些全局的配置：
```
// 设置全局的弹性
game.physics.p2.defaultRestitution = 0.8;

// 重力
game.physics.p2.gravity.y = 1200;
```

### 将sprite物理化
```
// 第二个参数为true的话能开启debug模式
game.physics.p2.enable(sprite, true);
// 注意物理化后该sprite的anchor会改为在中心
```


### 设置sprite的body
静止：
```
sprite.body.static = true;
```

边界：
```
// 清空shape
sprite.body.clearShapes()
// 添加圆形边界
sprite.setCircle(5)
// 或添加多边形边界
sprite.body.loadPolygon('physicsData', 'bunny');
```

### 添加约束(constrain)
```
var revolute = game.physics.p2.createRevoluteConstraint(lastComp, [0, -height/2], newComp, [0, height/2], maxForce);
```

### 移动与旋转
```
// 设置向下的速度
sprite.body.moveDown(300);

// 设置向左的旋转速度
sprite.body.rotateLeft(5);
```

```
// 速度归零
sprite.body.setZeroVelocity();
```

### body的信息
取得body所属的sprite名称：
```
body.parent.sprite.key
```

### body的常用设置：
```
// 0抗阻
sprite.body.setZeroDamping();

// 修正旋转
sprite.body.fixedRotation = true;
```

## 镜头
```
game.camera.follow(sprite);
```

## 控制
### 点击
监听点击：
```
// clickSomething是响应事件
game.input.onDown.add(clickSomething, this);
```

#### 命中测试
```
// 返回数组内的命中的body，pointer为click事件的参数
var bodies = game.physics.p2.hitTest(pointer.position, [bunny]);
```

### 键盘
#### 方向
在`create`中创建一个cursor
```
cursors = game.input.keyboard.createCursorKeys();
```

然后在update中使用：
```
    if (cursor.left.isDown) {

    }
    ```