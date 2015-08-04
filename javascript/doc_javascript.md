# Doc: Javascript

### Builtins
内置的类、方法、语法等：https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects

## 正则
参考：https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions

### 使用string的match方法

```
function getEpisodesByString(str) {
  var re = /第.*集/i;
  var result = str.match(re);
  return result;
}

console.log(getEpisodesByString('balbal第11集efjiejfi'));
// 输出[ '第11集', index: 6, input: 'balbal第01集efjiejfi' ]

console.log(getEpisodesByString('balbal第11efjiejfi'));
// 输出null
```

### 匹配多行

* 使用`m`来开启多行匹配
* `.`不能匹配换行，匹配所有字符可使用`\s\S`

可查看：http://stackoverflow.com/questions/1979884/how-to-use-javascript-regex-over-multiple-lines

例子：
```
var ss= "<pre>aaaa\nbbb\nccc</pre>ddd";
var arr= ss.match( /<pre[\s\S]*?<\/pre>/gm );
alert(arr);     // <pre>...</pre> :)
```


## eventInit+dispatchEvent与jquery中trigger的不同
两者并非完全相同，有些网页只接受前者，或者原生js的element.click()；jquery的trigger却是不能触发事件的。如新浪博客登陆。

http://stackoverflow.com/questions/11394529/is-there-any-difference-between-initeventdispatchevent-and-jquerys-triggercl

https://developer.mozilla.org/en-US/docs/Web/API/Event/initEvent

http://web.jaxedit.com/post/2013/03/30/2990442.html

http://oopschen.github.io/article/2013-06-17/webkit-keyboardevent.html

## Promise
参考：
* http://www.html-js.com/article/Learn-JavaScript-every-day-to-understand-what-JavaScript-Promises
* 研究：http://www.infoq.com/cn/articles/promise-a-misunderstanding-and-practical
* Q：https://github.com/kriskowal/q

## 事件
参考：http://code.tutsplus.com/tutorials/using-nodes-event-module--net-35941
文档：https://nodejs.org/api/events.html#events_events

### 基础用法

```javascript
var EventEmitter = require("events").EventEmitter;
 
var ee = new EventEmitter();
ee.on("someEvent", function () {
    console.log("event has occured");
});
 
ee.emit("someEvent");
```
