# 前端操作小技巧
## JS部分
### 1.快速字符串，数字互转：
#### const number = '10';
#### number = +number;
#### console.log(number); // 10

#### const number2 = 10;
#### number2 = number2+'' ;
#### console.log(number2 ); // '10'

### 2.快速浮点数转整数：
#### console.log(10.9 | 0);  // 10
#### console.log(-10.9 | 0); //- 10

### 3.数组去重方式
#### Array.prototype.unique = function() {
####     return [...new Set(this)];
#### }
#### var array = [1, 2, 3, 43, 45, 1, 2, 2, 4, 5];
#### array.unique();
#### 备注：
#### Set和Map类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在Set中，没有重复的key。
#### 要创建一个Set，需要提供一个Array作为输入，或者直接创建一个空Set：
#### var s1 = new Set(); // 空Setvar s2 = new Set([1, 2, 3]); // 含1, 2, 3
#### 重复元素在Set中自动被过滤：
var s = new Set([1, 2, 3, 3, '3']);
s; // Set {1, 2, 3, "3"}

### 4.数组映射
#### const cities = [
####     { name: 'Paris', visited: 'no' },
####     { name: 'Lyon', visited: 'no' },
####     { name: 'Marseille', visited: 'yes' },
####     { name: 'Rome', visited: 'yes' },
####     { name: 'Milan', visited: 'no' },
####     { name: 'Palermo', visited: 'yes' },
####     { name: 'Genoa', visited: 'yes' },
####     { name: 'Berlin', visited: 'no' },
####     { name: 'Hamburg', visited: 'yes' },
####     { name: 'New York', visited: 'yes' }
#### ];

#### const cityNames = Array.from(cities, ({ name}) => name);
#### console.log(cityNames);
#### // 输出 ["Paris", "Lyon", "Marseille", "Rome", "Milan", "Palermo", "Genoa", "Berlin", "Hamburg", "New York"]

### 5.快速删除数组元素
#### arr.splice(arr.findIndex(item => item.id === 8), 1)

### 6.随机生成字母和数组的组合
#### Math.random().toString(36).substr(2);

### 7.接收函数返回的多个结果
#### 在下面的代码中，我们从/post中获取一个帖子，然后在/comments中获取相关评论。由于我们使用的是async/await，函数把返回值放在一个数组中。而我们使#### 用数组解构后就可以把返回值直接赋给相应的变量。

#### async function getFullPost() { 
####     return await Promise.all([
####         fetch('/post'), 
####         fetch('/comments')
####     ]); 
#### } const [post, comments] = getFullPost();

### 8.数值交换

#### let param1 = 1;
#### let param2 = 2;
#### [param1, param2] = [param2, param1];
#### console.log(param1) // 2
#### console.log(param2) // 1

#### 9.合并对象
#### ES6带来了扩展运算符（...）。它一般被用来解构数组，但你也可以用它处理对象。
#### 接下来，我们使用扩展运算符来展开一个新的对象，第二个对象中的属性值会改写第一个对象的属性值。比如object2的b和c就会改写object1的同名属性。

#### let object1 = {a:1,b:2,c:3}
#### let object2 = {b:30,c:40,d:50}
#### let merged = {...object1,...object2}
#### console.log(merged)//{a: 1, b: 30, c: 40, d: 50}
#### let arr1 = [1,2,3]
#### let arr2 = [4,5,6]
#### let mergedArr = [...arr1,...arr2]
#### console.log(mergedArr)//1,2,3,4,5,6

### 10.js-按照某个属性排序数组里的元素(sort排序法)
#### let a = [{name:'Konges',age:20},{name:'pander',age:21},{name:'jiang',age:22}]
#### a.sort(function(a,b){return b.age-a.age})//降序 b>a b在a前面
#### console.log(a)//[{name:'jiang',age:22},{name:'pander',age:21},{name:'Konges',age:20}]
#### 11.vue中nextstick使用：
####  this.$nextTick(() => {
#### //这里执行关于DOM的操作内容（例如我们使用swiper的时候）
####  })
#### 用法：在下次DOM更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的DOM。

### 12.vue中this.$forceUpdate()强制刷新渲染页面

#### 由于一些嵌套特别深的数据，导致数据更新了，但是页面却没有重新渲染。我遇到的一个情况是，v-for遍历数据渲染，当方法中处理相应数组数据时，数组改变了，但是页面却没有重新渲染。

#### 解决方法：运用 this.$forceUpdate()强制刷新，解决v-for更新数据不重新渲染页面。

#### 官方解释：迫使 Vue 实例重新渲染。注意它仅仅影响实例本身和插入插槽内容的子组件，而不是所有子组件。

### 13.清空数组

#### 有时我们需要清空一个数组，比如用户点击了清空购物车。可以一条一条地删除，但是很少有这么可爱的程序员，哈哈。其实一行代码就能搞定，那就是直接将之length设置成0
#### var fruits = ["banana", "apple", "orange", "watermelon", "apple", "orange", "grape", "apple"];
#### fruits.length = 0;
#### console.log(fruits); // returns []

### 14.lastIndexOf()

#### 很多时候我们查找元素是否存在于某个数组中，经常使用indexOf方法，常常忽略lastIndexOf方法，后者会被使用的一个场景就是，某个数组中有重复的数据。
#### var nums = [1, 5, 2, 6, 3, 5, 2, 3, 6, 5, 2, 7];
#### var lastIndex = nums.lastIndexOf(5);
#### console.log(lastIndex); // returns 9

## CSS部分
### 1.下拉箭头：

### css3 实心下拉

#### #triangle-down {
####     width: 0;
####     height: 0;
####     border-left: 50px solid transparent;
####     border-right: 50px solid transparent;
####     border-top: 100px solid red;
#### }

### css3 有边框下拉

#### #triangle-down{
####     width: 10px;
####     height: 10px;
####     border: 2px solid #e8c16d;
####     border-left: 0;
####     border-bottom: 0;
####     -webkit-transform: rotate(135deg);
####     -ms-transform: rotate(135deg);
####     transform: rotate(135deg);
#### }

### 2.最容易记住的水平垂直居中：

#### #test{
#### position:absolute;
#### left:0;
#### top:0;
#### right:0;
#### bottom:0;
#### margin:0 auto;
#### }
#### 或者

#### #test{
#### position:absolute;
#### left:50%;
#### top:50%;
#### transform:translate(-50%,-50%);
#### -webkit-transform:translate(-50%,-50%);
#### margin:0 auto;
#### }

#### 3.边框模糊效果：
#### box-shadow: 0px rem(3) rem(20) #0197fd,0px 0px rem(20) #0197fd inset;


#### 3.【Animate.css】CSS动画库
#### https://daneden.github.io/animate.css/
