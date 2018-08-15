# javascript 闭包

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
