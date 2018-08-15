# javascript 闭包

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [javascript 闭包](#javascript-闭包)
	* [词法作用域](#词法作用域)
	* [闭包](#闭包)

<!-- /code_chunk_output -->

## 词法作用域

``` javascript
function init() {
    var name = "sixlib"; // name 是一个被 init 创建的局部变量
    function displayName() { // displayName() 是内部函数,一个闭包
        alert(name); // 使用了父函数中声明的变量
    }
    displayName();
}
init();
```

`displayName()`内的`alert()`显示额父级函数中声明的`name`变量值。

## 闭包

``` javascript
function makeFunc()
{
    var name='sixlib';
    function displayName()
    {
        alert(name);
    }
    return displayName;//displayName()被外部调用
}
var myFunc=makeFunc();//创建displayName()实例引用
myFunc();
```

`myFunc`是执行`makeFunc`时创建的`displayName`函数实例的引用，而`displayName`实例仍可访问其词法作用域中的变量，即可以访问到`name`。由此，当`myFunc`被调用时`name`仍可被访问。

``` javascript
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12
```

