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
###当没有以绝对路径或相对路径来指向文件的时候，那么这个加载的模块要么是内置模块要么是第三方模块(在node_modules)
###当查找内置模块或者第三方模块的时候，执行的步骤如下
1. 先在内置模块里面查找，找不到按照下面方式去查找
2. 获取module.paths里面的第一个目录查找
3. 尝试添加.js, .json文件进行查找
4. 如果还是找不到，会尝试将require的参数当成包来查找,查找package.json文件里面的main属性对应的模块，如果有该模块的话直接获取该模块;如果没有的话,在该包下面尝试查找index.js,index.json
5. 如果还是找不到的话，会继续查找module.paths里面的下一个目录，当所有的目录都找完了，还是找不到的话，就会报错

##6.nodejs中exports和module.exports的区别
1. node帮我们实现了exports = module.exports = {}
2. 当加载模块的时候，模块执行完返回的结果就是module.exports
3. 如果直接在exports或module.exports添加属性或者的时候，是没有区别的
4. 如果改变exports的值或者引用地址的时候，这个时候exports就不等于module.exports,

##7.自定义一个npm包并且发布到npm官网上面去
1. 新建一个新的`github`仓库，把本地自定义的包推到远程仓库
2. 在自定义包里面执行`npm init`新建package.json文件;
3. npm publish发布自己的包
4. 如果发布成功的话，就可以在项目里面以第三方模块的方式安装了

> 注意: name名称不能包含大写字母和中文，最好起特殊意义的名字，确保此包在官网没有被注册过，不然会报错; 每次发布的时候`npm publish`的时候，version一定要确保比之前的版本大
> 此过程可能会遇到一些问题:确保自己使用的npm镜像是npm官网的; 确保自己已经注册了npm用户,并且命令行已经登录了(具体步骤百度)

##8.进程和线程的关系
1. 进程是应用程序在处理机上面的一次运行过程，线程是进程的一部分，一个进程包含多个线程在运行

##9.异步和同步
1. 异步就是任务不连续执行
2. 同步就是任务连续执行



















