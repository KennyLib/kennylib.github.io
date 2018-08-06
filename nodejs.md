    

# 问题

- 什么是错误优先回调函数？

- 如何避免回调地狱？

- 什么是Promise？

- 用什么工具保证一直的代码风格？ 为什么要这样？

- 什么是Stub？举例说明

- 什么是测试金字塔？举例说明

- 最喜欢哪个HTTP框架？举例说明

- Cookies为如何防范XSS攻击？

- 如何保证依赖的安全性？

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
    
    