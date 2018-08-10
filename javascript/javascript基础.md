# Javascript 基础

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [Javascript 基础](#javascript-基础)
	* [JavaScript 对象](#javascript-对象)
		* [Array 对象](#array-对象)
			* [对象属性](#对象属性)

<!-- /code_chunk_output -->

## JavaScript 对象

### Array 对象

``` javascript
var arr = ['Saab', 'Volvo', 'BMW']
```

#### 对象属性

- JavaScript concat()方法

连接多个数组，不破坏源数组的情况下生成新的数组

``` javascript
var hege = ["Cecilie", "Lone"];
var stale = ["Emil", "Tobias", "Linus"];
var kai = ["Robin"];
var children = hege.concat(stale,kai);
console.log(children)
//children 输出 Cecilie,Lone,Emil,Tobias,Linus,Robin
```

- every()方法

验证数组中元素是否满足条件,返回值 boolean类型；**不能对空数组进行检测**

``` javascript
var ages = [32, 33, 16, 40];

function checkAdult(age) {
    return age >= 18;
}
console.log(ages.every(checkAdult))
//输出false
```

- filter()方法

创建一个新数组，新数组是指定数组中满足条件的远足组成的数组；

``` javascript
var ages = [32, 33, 16, 40];

function checkAdult(age) {
    return age >= 18;
}
console.log(ages.filter(checkAdult))
//输出 ： 32，33，40
```

- forEach()方法

用于调用数组中的每一个元素，并将元素传递给回调函数。**对空数组不调用回调函数的。**

``` javascript
var numbers = [4, 9, 16, 25];
function myFunction(item, index) {
     console.log(item) 
}
numbers.forEach(myFunction)
/**
 * 输出：
 * 4
 * 9
 * 16
 * 25
 */
```

- indexOf()方法

返回数组中某个指定元素第一次出现的位置；**没有找到指定元素则返回-1。**

``` javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.indexOf("Apple"))
//输出 2

console.log(fruits.indexOf("pint"))
//输出 -1
```

- isArray()方法

判断一个对象是否是数组；返回boolean类型值。

``` javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(Array.isArray(fruits));
//输出： true
console.log(Array.isArray({}));
//输出： false
```

- join()方法

将数组中所有元素转换成一个字符串。

``` javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.join())
//输出： Banana,Orange,Apple,Mango
```

- lastIndexOf()方法

在一个数组中从后向前搜索，返回一个指定元素在数组中最后出现的位置。**没有找到指定元素则返回-1。**

``` javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.lastIndexOf("Apple"))
//输出 2

console.log(fruits.lastIndexOf("pint"))
//输出 -1
```
