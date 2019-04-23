## 作用域
使用了默认参数后，函数进行声明初始化时，参数会形成一个单独的作用域（context）。等到初始化结束，这个作用域就会消失。

函数体内使用到参数时，如果声明中没有该参数，则会去全局变量中查找该参数


```javascript
let x = 1;

function f(y = x) {//参数作用域中没有x,则去全局作用域中找
  let x = 2;
  console.log(y);
}

f() // 1
```


## 箭头函数
1，由于大括号被解释为代码块，所以如果箭头函数直接返回一个对象，必须在对象外面加上括号，否则会报错


```javascript
let getTempItem = id => ({ id: id, name: "Temp" });
```

2，如果箭头函数只有一行语句，且不需要返回值

```javascript
let fn = () => void doesNotReturn();
```
3，注意事项

>
>（1）函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。
> 
> <font size=2 color=#803df9>注
：this指向的固定化，并不是因为箭头函数内部有绑定this的机制，实际原因是箭头函数根本没有自己的this，导致内部的this就是外层代码块的this。正是因为它没有this，所以也就不能用作构造函数。</font>
>
> <font size=2 color=#c7254e>ps： this、arguments、super、new.target在箭头函数之中都不存在的，而是指向外层函数的对应变量。</font>
> 
>
> （2）不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。
> 
> （3）不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。
> 
> （4）不可以使用yield命令，因此箭头函数不能用作 Generator 函数。

#### 不适用场合

##### 1，定义对象的方法中不适用。

因为对象不构成单独的作用域，导致jumps箭头函数定义时的作用域就是全局作用域

```javascript
const cat = {
  lives: 9,
  jumps: () => {
    this.lives--;
  }
}
```
#####  2，需要动态this

```javascript
//this指向全局对象
button.addEventListener('click', () => {
  this.classList.toggle('on');
});
```






