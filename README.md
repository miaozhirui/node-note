#(以下是自己的理解，如果有错误请提出改正，谢谢!)

##1.nodejs可以直接访问的变量
```
__dirname ,__filename ,exports ,require, module 还有global下面所有的变量
```
##2.I/O读写速度
1. cpu > 内存 > 硬盘 > 光盘 > 网络请求
##3.同步执行and异步执行
1. 同步执行:cup执行任务的时候，安装顺序执行，前面任务执行了，后面的任务才能别执行，如果前面的任务执行时间比较长的话，后面的任务就一直等着
2. 异步执行:cup跳过需要等待很长时间的任务，执行后面的任务

##4.js异步执行的运行机制
1. js主线程是单线程的,程序执行的时候会形成`执行栈`,当遇到异步任务的时候，会把异步任务放到任务队列(事件队列)里面,当执行栈任务执行完的时候，开始执行任务队列，这个过程是循环的，称为`事件循环`

##5.node里面的require查找规则
###当没有以'/'和'./'来指向文件的时候，那么这个加载的模块要么是内置模块要么是第三方模块(在node_modules)
###当查找内置模块或者第三方模块的时候，执行的步骤如下
1. 获取module.paths里面的第一个目录查找
2. 尝试添加.js, .json文件进行查找
3. 如果还是找不到，会尝试将require的参数当成包来查找,查找package.json文件里面的main属性对应的模块，如果有该模块的话直接获取该模块;如果没有的话,在该包下面尝试添加.js,.json来查找
4. 如果还是找不到的话，会继续查找module.paths里面的下一个目录，当所有的目录都找完了，还是找不到的话，会尝试查找系统模块，如果这个时候再找不多，就会报错




















