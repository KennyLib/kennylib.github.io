
# 问题

- 什么是错误优先回调函数？

- 如何避免回调地狱？

- 什么是Promise？

- 用什么工具保证一直的代码风格？ 为什么要这样？

- 什么是Stub?举例说明

- 什么是测试金字塔?举例说明

- 最喜欢哪个HTTP框架?举例说明

- Cookies如何防范XSS攻击?

- 如何保证依赖的安全性?

# 答案

- 什么是错误优先的回调函数？

    错误优先的回调函数（Error-Frist Callback）用于同步时返回错误和数据，第一个参数错误，并且验证它是否出错；其他参数用于返回数据。
    ``` node
    fs.readfile(filePath, function(err,data){
        if(err){
            //处理错误
            return console.log(err);
        }
        console.log(data)
    })
    ```

- 如何避免回调地狱？

  以下方式可以避免回调地狱：
  1. 模块化：将回调函数转换成独立的函数
  2. 使用流程控制库，例如[async](https://npm.taobao.org/package/async)
  3. 使用Promise
  4. 使用async/await([参考async/await替换Promise的6个理由](https://blog.fundebug.com/2017/04/04/nodejs-async-await/))

- 什么是Promise?
    Promise可以帮助我们更好的处理异步操作.下面的实例中，100ms后悔打印result字符串，catch用于错误处理。多个Promise可以连接起来。
    ``` node
    new Promise((resolve, reject) =>
    {
        setTimeout(() => {
            resolve('result');
        }, 100)
    })
    .then(console.log('log'))
    .catch(console.error('err')
    ```

- 用什么工具保证一致的代码风格？为什么要这样？
    团队协作时，保证一致的代码风格重要的，这样团队成员才可以更快的修改代码，而不需要每一次去适应新的风格。这些根据可以帮助我们：
    1. ESlint
    2. Standard
    感兴趣的话，可以参考[Javascript Clean Coding](https://blog.risingstack.com/javascript-clean-coding-best-practices-node-js-at-scale/)

- 什么是Stub?举例说明
    Stub用于模拟模块的行为。测试时，Stub可以为函数电泳返回模拟的结果。比如说，当我们写文件时，实际上并不需要咋整去写。
    ``` node
    var fs = require('fs');
    var writeFileStub = sinon.stub(fs, 'writeFile', function(path, data, cb)
    {
        return cb(null);
    });
    expect(writeFileStub).to.be.called;
    writeFileStub.restore();
    ```
