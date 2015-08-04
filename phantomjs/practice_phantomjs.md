# 实战：Phantomjs

### 获取用户输入
http://stackoverflow.com/questions/16452131/is-there-a-way-to-read-user-input-from-keybord-for-phantomjs

```
 var system = require('system');

 system.stdout.writeLine('CaptchaCode: ');
 var line = system.stdin.readLine();
```
