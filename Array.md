# Новые методы массивов в ES6

A cheatsheet containing ECMAScript 6’s new and old array methods 

## Table of Contents

- [Static methods](#static-methods)
    - [Array from](#array-from)
    - [Array of](#array-of)
- [Prototype methods](#prototype-methods)
    - [Iterating over arrays](#iterating-over-arrays)
    - [Searching for array elements](#searching-for-array-elements)
    - [Array.prototype.fill()](#array-prototype-fill)
    - [Array.prototype.copyWithin()](#array.prototype.copyWithin())
- [Subclassing](#subclassing)
    - [Accessing and setting](#accessing-and-setting)

## Static methods
Класс `Array` получил два своих собственых метода - Array.from() и Array.of().

#### Array from
> ECMAScript 2015 - Standart

> Метод Array.from() создаёт новый экземпляр Array из массивоподобного или итерируемого объекта.

> В ES6 классовый синтаксис позволяет создавать подклассы как встроенных классов, так и классов,
определённых пользователем; в результате статические методы класса, вроде Array.from «наследуются»
подклассами Array и создают новые экземпляры подкласса, а не класса Array.

```javascript
Array.from(arrayLike, *mapFunc, *thisArg)
```
#### Array of
> ECMAScript 2015 - Standart

Метод `Array.of()` создаёт новый экземпляр массива Array из произвольного числа агрументов,
вне зависимости от числа или типа аргумента.

```javascript
Array.of(element0[, element1[, ...[, elementN]]])
```

## Prototype methods
#### Iterating over arrays

> `Array.prototype.entries()` -> ES6 Standart

```javascript
var arr = ['a', 'b', 'c'];
var eArr = arr.entries();

console.log(eArr.next().value); // [0, 'a']
console.log(eArr.next().value); // [1, 'b']
console.log(eArr.next().value); // [2, 'c']
```

> `Array.prototype.keys()` -> ES6 Standart

```javascript
var arr = ['a', 'b', 'c'];
var iterator = arr.keys();

console.log(iterator.next()); // { value: 0, done: false }
console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: undefined, done: true }

var arr = ['a', , 'c'];
var sparseKeys = Object.keys(arr);
var denseKeys = [...arr.keys()];
console.log(sparseKeys); // [0, 2]
console.log(denseKeys);  // [0, 1, 2]
```

> `Array.prototype.values()` -> ES6 Standart

```javascript
var arr = ['a', 's', 'd'];
var eArr = arr.values();

for (let letter of eArr) {
  console.log(letter);
}

var arr = ['a', 's', 'd'];
var eArr = arr.values();
console.log(eArr.next().value); // a
console.log(eArr.next().value); // s
console.log(eArr.next().value); // d
```


#### Searching for array elements

> ECMAScript 2015 - Standart

An example of using `var`:

```javascript
Array.prototype.find()
Array.prototype.findIndex()
```

#### Array prototype fill

> ECMAScript 2015 - Standart

```javascript
Array.prototype.fill(value, *start, *end)
```

#### Array.prototype.copyWithin()

> ECMAScript 2015 - Standart

Метод copyWithin() копирует последовательность элементов массива внутри него в позицию,
начинающуюся по индексу target. Копия берётся по индексам, задаваемым вторым и третьим
аргументами start и end. Аргумент end является необязательным и по умолчанию равен длине массива.

```javascript
arr.copyWithin(target, start[, end = this.length])
```

## Subclassing
`Array` is subclassable

#### Accessing and setting

```javascript
function() {
  class C extends Array {}
  var c = new C();
  var len1 = c.length;
  c[2] = 'foo';
  var len2 = c.length;
  return len1 === 0 && len2 === 3;
}

function() {
  class C extends Array {}
  var c = new C();
  c[2] = 'foo';
  c.length = 1;
  return c.length === 1 && !(2 in c);
} 
```

