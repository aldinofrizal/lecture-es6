# lecture-es6

## Table of Contents
1. [Use Strict](#use-strict)
2. [Array & Object Reference](#array-and-object-reference)
3. [Arrow Function](#arrow-function)
4. [Module Export](#module-export)
5. [Basic Desctructuring](#basic-destructuring)
6. [Process.argv](#processargv)
7. [Built-in Function](#built-in-function)


## [Use Strict](https://www.w3schools.com/js/js_strict.asp)

Run javascript into strict mode, can be declared globally or locally (inside function)
- Using an object & variable, without declaring it
- Duplicating a parameter name
- Using booked name (with, arguments, etc) as variable
<br><br>

## [Array and Object Reference](https://codeburst.io/explaining-value-vs-reference-in-javascript-647a975e12a0)

Variables that are assigned a non-primitive value are given a reference to that value. That reference points to the object’s location in memory. The variables don’t actually contain the value.

Javascript has 5 data types that are passed by value: Boolean, null, undefined, String, and Number. We’ll call these primitive types.

Javascript has 3 data types that are passed by reference: Array, Function, and Object. These are all technically Objects, so we’ll refer to them collectively as Objects.

```js
/// Primitive Data Types
var mobil = 'hello mobil'
var motor = 'hello motor'

var newMobil = mobil
var newMotor = motor

console.log(mobil, newMobil) //hello mobil hello mobil
console.log(motor, newMotor) //hello motor hello motor

newMobil = 'update mobil'
newMotor = 'update motor'

console.log(mobil, newMobil) //hello mobil update mobil
console.log(motor, newMotor) //hello motor update motor

```

```js
/// Object/Non Primitive Data Types
var newCars = cars

console.log(cars, newCars) // [ 'suzuki', 'honda' ] [ 'suzuki', 'honda' ]

newCars.push('Toyota')

console.log(cars, newCars) // [ 'suzuki', 'honda', 'Toyota' ] [ 'suzuki', 'honda', 'Toyota' ]


var specialCars = [...cars]

console.log(cars, specialCars) // [ 'suzuki', 'honda', 'Toyota' ] [ 'suzuki', 'honda', 'Toyota' ]

specialCars.push('BMW')

console.log(cars, specialCars) // [ 'suzuki', 'honda', 'Toyota' ] [ 'suzuki', 'honda', 'Toyota', 'BMW' ]
```
<br>


<br>

## Arrow Function
```js
// Cara menulis fungsi yang umum digunakan
function penjumlahan(param1, param2) {
  return param1 + param2;
}

// Alternatif cara menulis fungsi
var pengurangan = function (param1, param2) {
  return param1 - param2;
}

// Cara penulisan function dengan arrow function
let perkalian = (param1, param2) => {
  return param1 + param2;
}

// Bila akan langsung mereturn, arrow function tanpa curly bracket { }
let pembagian = (param1, param2) => param1 + param2;
```

<br><br>

## Module Export
```js
// multiple variable / function
// assign to object or array
module.exports = {
  penjumlahan,
  pengurangan,
  perkalian,
  pembagian
};

// single variable / function
module.exports = penjumlahan
```


<br>

## [Basic Destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

```js

let car = {
  id: 1,
  type: 'Baleno',
  brand: 'Suzuki',
  cc: 1500
}

let { type, brand: merek } = car

console.log(type, merek) // Baleno Suzuki

let movies = ['KKN Desa Penari', 'Dr Strange']

let [kkn] = movies

console.log(kkn) // KKN Desa Penari

```

<br>

## [process.argv](https://www.geeksforgeeks.org/node-js-process-argv-property/)
The process.argv property is an inbuilt application programming interface of the process module which is used to get the arguments passed to the node.js process when run in the command line.

Syntax:
```
process.argv
```

Return Value: This property returns an array containing the arguments passed to the process when run it in the command line. The first element is the process execution path and the second element is the path for the js file.

```js
let movies = process.argv
console.log(movies)

// node index.js
// [
//   '/home/aldinofrizal/.nvm/versions/node/v18.1.0/bin/node',
//   '/home/aldinofrizal/h8/lecture/lecture-es6/index.js'
// ]

// node index.js 'kkn desa penari' DrStrange   
// [
//   '/home/aldinofrizal/.nvm/versions/node/v18.1.0/bin/node',
//   '/home/aldinofrizal/h8/lecture/lecture-es6/index.js',
//   'kkn desa penari',
//   'DrStrange'
// ]
```


<br>

## [Built-in Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
### [Sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
```js
const numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers);

// [1, 2, 3, 4, 5]
```
### [Join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) & [Split](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
Join -> joining all array elements into string
Split -> spliting all array elements into array

```js
const str = 'The quick brown fox jumps over the lazy dog.';

let words = str.split(' ');

console.log(words)

// [
//   'The',   'quick',
//   'brown', 'fox',
//   'jumps', 'over',
//   'the',   'lazy',
//   'dog.'
// ]

let wordsJoin = words.join('x')

console.log(wordsJoin)

// Thexquickxbrownxfoxxjumpsxoverxthexlazyxdog.

```
### [For Each](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
loop through array
```js
const num = [1, 5, 12];

num.forEach(element => {
  console.log(element)
});

// expected output: "1"
// expected output: "5"
// expected output: "12"

```

### [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
Manipulated all array elements with same logic, and push it to new array
```js
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(array1, map1);
// expected output: Array [1, 4, 9, 16] Array [2, 8, 18, 32]
```
### [Filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
Create new array returning element with passed true on callback function
```js
const num = [1, 4, 9, 16];

const bigNum = num.filter(n => {
  return n > 8
})

console.log(bigNum)
// [ 9, 16 ]
```

### [Reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
Sum / add element to defined initial value
```js
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10
```
