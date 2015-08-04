# 实战：Protractor

# 简介

### 参考

# 安装与运行

首先，你需要安装protractor，推荐全局安装；安装后你能使用用两个命令工具，`protractor`及`webdriver-manager`：
```
npm install -g protractor
```

然后更新最新版的webdrier-manager：
```
webdriver-manager update
```

接下来就可以开始运行webdriver-manager：
```
webdriver-manager start
```

# 编写config文件与测试文件

# 测试

# jasmine参考

# protractor参考

### 取消angular限定
```
  beforeEach(function() {
      return browser.ignoreSynchronization = true;
        });
	```

### 测试alert
```
      var al = browser.switchTo().alert();
            al.then(function() {
	            expect(al.getText()).toEqual('请填写电话');
		            al.accept(); //确认alert，否则下面的页面测试会报错
			          });
				  ```

### 选择子元素及统计个数
```
    it('should have 9 options', function() {
          var carOptions = carSelect.all(by.tagName('option'));
	        expect(carOptions.count()).toBe(9);
		    });
		    ```

# 测试进阶

# 常见问题
#### 测试时timeout？
使用browser.driver的get方法而不是browser的get
