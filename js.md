# 基本的数据类型
- Number
- String
- Boolean
- Symbol
- Object
    - Function
    - Array
    - Date
    - RegExp
    - Map
    - Set
- null
- undefined

详：
```js
// 注释

/*
长注释 
*/

// 变量声明
var foo1;
const foo2;
let foo3; // block scope

// Boolean
true, false

// String
'a sentence' === "a sentence"; // 单双引号等价

// Object
let o1 = {
    "name": 123
};
let o2 = {
    'name': 123
};
let o3 = {
    name: 123
};
o1.name;
o1['name'];

delete o1['name'];
delete o2.name;

// Map
// 注： 普通的Object类型，只能用String作为key，而Map可以使用任意类型作为key。
m = new Map();
m = new Map([
    ['key1', 'value1'],
    [2, 'value2']
]);

// Set
s = new Set();
s = new Set([1, 2, 3, 3, 4]);


// function
function foo(arg1, arg2) {
    return 123;
}
// 箭头函数（arrow function）
const foo = (arg1, arg2) => {
    // body
    return ;
}
const foo2 = arg1 => arg1 * 2; // 单个参数可以不加括号。如果函数体仅包含一条语句，那么可以不加大括号，默认return。
const foo3 = (arg1, arg2) => ({label: arg1, value: arg2}) // 因为大括号被解释为代码块，如果要在一行语句中返回一个对象，需要加上圆括号
```


# 函数
```js
// 特殊变量arguments(array-like)
function avg() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
      sum += arguments[i];
    }
    return sum / arguments.length;
}

// Rest parameter syntax：所有多的参数自动组装成一个Array。
function avg(...args) {
    var sum = 0;
    for (let value of args) {
      sum += value;
    }
    return sum / args.length;
}

// 结合Object Destructuring的函数声明
function foo({first_name, last_name}) {

}
```

# 较新语法
```js
// Destructuring Array
const [a, b, c, d] = [1, 2, 3, 4];
// Destructuring Object
o = {
    foo: 'foo',
    bar: 'bar',
    baz: 'baz'
};
const {foo, bar} = o;

// template string
const a = 1
`a + 1 = ${a + 1}`

`multi-line
string.
`

// Spread syntax
// Array spread
const a = [1, 2, 3];
const b = [...a]; // 相当于：b = a.slice()
// Object spread
const o2 = {...o}; // 相当于 o2 = Object.assign({}, o);

// Computed property names
o3 = {
    [variable]: 123
};
```

# 语句
语句行末尾带不带分号均可。
控制语句
```js
// if
if (name === 'foo') {
    // body
}

// 循环
while (true) {
    // body
}

for (let i = 0; i < 5; i++) {
  // Will execute 5 times
}

for (let property in object) {

}

for (let item of iterator) {

}
/*for in 和 for of 的区别
for in is used to loop through properties of an object. It can be any object. for in allows you to access the keys of the object but doesn’t provide reference to the values. In JavaScript object properties themselves have internal properties. One of the internal properties is [[Enumerable]]. for in will only walkthrough a property if it has [[Enumerbale]] set to true. It not used to iterate elements of an collection rather used to iterate properties of objects.

for of is a new way for iterating collections. Its introduced in ES6. Earlier you had to use for or while loop to iterate through elements of an collection. For for of to work on an collection, the collection must have an [Symbol.iterator] property.
*/
```

# 类
```js
class Person {
    constructor(name, age, gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
    }

    incrementAge() {
      this.age += 1;
    }
}

// 关于this的注意点：
// 在 JavaScript 中，class 的method默认不会绑定 this。
// 方法一、使用this.foofunc.bind(this)来手动绑定。
// 方法二、使用public class fields语法，该语法自动绑定this。见下：
class LoggingButton extends React.Component {
    constructor(props) {
        super(props);
        this.handleClick = this.handleClick.bind(this);
    }

    handleClick() {
        console.log('this is:', this);
    }

    render() {
        return (
          <button onClick={this.handleClick}>
            Click me
          </button>
        );
    }
}

class LoggingButton extends React.Component {
    // 此语法确保 `handleClick` 内的 `this` 已被绑定。
    // 注意: 这是 *实验性* 语法。
    handleClick = () => {
        console.log('this is:', this);
    }

    render() {
        return (
          <button onClick={this.handleClick}>
            Click me
          </button>
        );
    }
}

```

# 模块
```js
/*
1. export 语句输出的接口与其对应的值是动态绑定的关系，即通过该接口可以取到模块内部实时的值。
2. import语句为singleton模式，多个重复import只会执行一次。
*/
export { foo1, foo2 };
import { foo1, foo2 } from 'bar';
import { foo3, foo3 } from './bar2';
// default
export default foo4;
import foo4 from 'bar3';

```

# 数据结构相关
## Array
```js
array = ['a', 'b', 'c']
// 基本
array.length
array.push('d')
array.pop()
array.splice() // array.splice(start[, deleteCount[, item1[, item2[, ...]]]])：在任意的位置给数组添加或删除任意个元素。

// enumerate
for (const [index, valur] of array.entries()) {
    // body
}

// slice
array.slice(1, 3); // 和python中的array[1:3]一样：左闭右开，浅拷贝。

// concatnate
array = array.concat(['d', 'e']); // 注意：.concat()并不改变调用该方法的数组，而是返回一个新的array

// reverse
array.reverse() // 原地逆序（会改变原数组）
array.slice().reverse() // 不改变原数组，获得一个新的逆序数组。

// map
const array2 = array.map((item, index) => {
    // body
    return ;
})

// 浅复制
const copy = array.slice();
const copy2 = [...array];
```

## Object
```js
o = {
    'a': 'A',
    'b': 'B'
}


// 遍历
for (const [key, value] of Object.entries(o)) {
    console.log(`${key}: ${value}`);
}
Object.keys()
Object.values()
// 注意和Array不一样，.entries，.keys()，.values()方法均是类方法（静态？），不是实例方法。所以无法在Object实例上调用。

// 构造Object
const o = Object.fromEntries([
    ['key1', 'value1'],
    ['key2', 'value2']
])

// 浅复制
const copy = Object.assign({}, o);
const copy2 = {...o};
```
