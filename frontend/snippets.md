# 前端实用代码片段

### chrome控制台显示Cartman图片

```
  -function showCartman() {
      var location = window.location;
          var cartman = location.origin + location.pathname + 'source/images/cartman.jpg';
	      console.log('%c', 'padding: 76px 115px; line-height: 152px; background-image: url("' + cartman + '"); background-size: 100%; background-repeat: no-repeat; background-position: center center;');
	        } ();
		```

### Lazy Loading

```
  function loadImg(selector, parent) {
      parent.find(selector).each(function(){
            var jqElm = $(this);
	          if (!jqElm.attr('src')) {
		          var src = jqElm.attr( "data-original" );
			          jqElm.attr('src', src);
				        }
					    })
					      }
					      ```