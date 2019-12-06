```js
/* 不可变性（Immutable）
不可变性在 React 中非常重要，原因
1. 便于React确定数据缺失发生了改变：如果直接修改数据，那么就很难跟踪到数据的改变。跟踪数据的改变需要可变对象可以与之改变之前的版本进行对比，这样整个对象树都需要被遍历一次。
跟踪不可变数据的变化相对来说就容易多了。如果发现对象变成了一个新对象，那么我们就可以说对象发生改变了。

2. 不可变性最主要的优势在于它可以帮助我们在 React 中创建 pure components。我们可以很轻松的确定不可变数据是否发生了改变，从而确定何时对组件进行重新渲染。
*/

/* 列表key值
每一个组件列表都要有一个key值，React根据key值来确定哪些项发生了改变（增加、删除、重新排序或者更新列表项）。
组件的 key 值并不需要在全局都保证唯一，只需要在当前的同一级元素之前保证唯一即可。
*/

// 函数
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
// 使用解构赋值
function Welcome({name}) {
  return <h1>Hello, {name}</h1>;
}
// 特殊的参数props.children

```