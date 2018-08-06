# 特点

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

## 异步 I/O

在nodejs中，绝大多数的操作都是以异步的方式进行调用。 **每个调用之间不用等待之前的I/O调用结束。** 在编程模型上可以极大的提高效率。下面的两个文件读取任务的耗时取决于最慢的那个文件读取的耗时：

``` node
fs.readFile('/path1',function(err,file)
{
    console.log('读取文件1完成')
})
fs.readFile('/path2',function(err,file)
{
    console.log('读取文件2完成')
})
```

而对于同步I/O而言，它们的耗时是两个任务的耗时之和。这里异步带来的优势是显而易见的。

## 事件与回调函数

nodejs 将前端浏览器中应用广泛的且成熟的事件引入后端，配合异步I/O，将事件点暴露给业务逻辑。
下面的例子展示的是Ajax异步提交的服务器端处理过程。Node创建一个Web服务器，并侦听8080端口。对于服务器，我们为其绑定了request事件，对于请求对象，我们为其绑定了data事件和end事件：

``` node
var http = require('http')
var querystring = require('querystring')

//侦听服务器的request事件
http.createServer(function(req, res)
{
    var postData = ''
    req.setEncoding('utf8')
    //侦听请求的data事件
    req.on('data',function(chunk)
    {
        postData += chunk
    })

    //侦听请求的end事件
    req.on('end', function()
    {
        res.end(postData)
    })
}).listen(8008)
console.log('服务器启动完成')
```

事件的编程方式具有轻量级、松耦合、只关注事物点灯优势，但是在多个异步任务的场景下，事件与事件之间各自独立，如何写作是一个问题。

Node除了异步和事件外，回调函数是一个大特色，也是最好的接收异步调用返回数据的方式。

## 单线程