# HOW TO: 使用mocha与chai进行测试

```
mocha官网：http://visionmedia.github.io/mocha/
chai API: http://chaijs.com/api/
一个不错的教程：http://code.tutsplus.com/tutorials/testing-in-nodejs--net-35018
使用makefile：http://fengmk2.cnpmjs.org/ppt/unittest-and-bdd-in-nodejs-with-mocha.html
使用makefile2：http://www.lescentslignes.com/makefiles-in-node.html
makefile3：http://oxy.fi/2013/02/03/how-to-use-makefiles-in-your-web-projects/
```

## 准备
首先你当然要安装mocha：
```
sudo npm install -g mocha
```

你需要专门的语法模块来方便测试，例如chai：
```
npm install chai
```

可以使用专门的yo插件来生成测试文件模板：generator-create-test。安装：

```
npm install -g yo
npm install -g generator-create-test
```

## 编写测试文件

然后就可以用`yo create-test`来生成一个测试文件模板：

```
yo create-test testDemo

// testDemo.js
```

修改testDemo.js：

```javascript
var assert = require("assert")
describe('Array', function(){
  describe('#indexOf()', function(){
      it('should return -1 when the value is not present', function(){
            assert.equal(-1, [1,2,3].indexOf(5));
	          assert.equal(-1, [1,2,3].indexOf(0));
		      })
		        })
			})
			```

运行：`mocha testDemo.js`