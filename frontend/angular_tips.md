# Angular小tips

### directive中各方法的运行顺序

假如我们有3个directive：A、B和C。其中A在外层，而B、C同级（B先C后），那么：
* A的controller运行
* A的link运行
* B的controller运行
* B的controller中emit的消息响应成功
* B的link运行
* C的controller运行
* C的link运行
