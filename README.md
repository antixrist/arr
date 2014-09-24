This is JavaScript Array extended. It can throw event ```change```. You can use it for something like [Backbone Collection](http://backbonejs.org/#Collection).



new Arr()
=========

Initialize new array.



Properties
==========

events
------

List of Attached Events.

```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.on('change', function(event) {
  console.log('fruits list is changed.');
});

// fruits.events
// [{
//  "name": "change",
//  "handler": function() { ... }
// }]

fruits.push('mango');
// fruits list is changed.
// fruits
// ['apple', 'orange', 'pineapple', 'mango']
```

length
------

Standard property [```length```](Standart accessor methods supported).



Accessor methods
================

get(index [, defaultValue])
---------------------------

Example:
```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.get(0);
// apple

fruits.get(10, 'lime'); // trying to get undefined element - return defaultValue
// lime

fruits.get(20); // trying to get undefined element
// null
```

Standard accessor methods are supported
---------------------------------------

* [```concat()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) Returns a new array comprised of this array joined with other array(s) and/or value(s).
* [```join()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) Joins all elements of an array into a string.
* [```slice()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) Extracts a section of an array and returns a new array.
* [```toString()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) Returns a string representing the array and its elements. Overrides the ```Object.prototype.toString()``` method.
* [```toLocaleString()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toLocaleString) Returns a localized string representing the array and its elements. Overrides the ```Object.prototype.toLocaleString()``` method.
* [```indexOf()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) Returns the first (least) index of an element within the array equal to the specified value, or -1 if none is found.
* [```lastIndexOf()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) Returns the last (greatest) index of an element within the array equal to the specified value, or -1 if none is found.

and [others](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array#Accessor_methods).



Mutator methods
===============

set(index, value)
-----------------

Set value by index. Will be triggered event ```change```.

Example:
```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.set(0, 'banana');
// ['banana', 'orange', 'pineapple']

fruits.get(1, 'lime');
// ['banana', 'lime', 'pineapple']

fruits.get(3, 'nut');
// ['banana', 'lime', 'pineapple', 'nut']
```

update(handler)
---------------

Update one or more items. Will be triggered event ```change```.

Example:
```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.update(function(value, index) {
  if (index === 2) {
    return 'lime';  // "return" not undefined value for update item
  }
});
// ['apple', 'orange', 'lime']

fruits.update(function(value, index) {
  return index;
});
// [0, 1, 2]
```

Standard mutator methods are supported
--------------------------------------

Each mutator method throw event ```change```. How? You can read in section Events.

* [```pop()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) Removes the last element from an array and returns that element.
* [```push()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) Adds one or more elements to the end of an array and returns the new length of the array.
* [```reverse()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first.
* [```shift()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) Removes the first element from an array and returns that element.
* [```sort()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) Sorts the elements of an array in place and returns the array.
* [```splice()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) Adds and/or removes elements from an array.
* [```unshift()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) Adds one or more elements to the front of an array and returns the new length of the array.

and [others](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array#Mutator_methods).



Iteration methods
=================

* [```forEach()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) Calls a function for each element in the array.
* [```every()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) Returns true if every element in this array satisfies the provided testing function.
* [```some()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) Returns true if at least one element in this array satisfies the provided testing function.
* [```filter()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) Creates a new array with all of the elements of this array for which the provided filtering function returns true.
* [```map()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) Creates a new array with the results of calling a provided function on every element in this array.
* [```reduce()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) Apply a function against an accumulator and each value of the array (from left-to-right) as to reduce it to a single value.
* [```reduceRight()```](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) Apply a function against an accumulator and each value of the array (from right-to-left) as to reduce it to a single value.

and [others](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods).

You can use method ```filter()``` for searching items by conditions.

Example:
```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

var fruitsWithWordApple = fruits.filter(function(value, index) {
  if (value.indexOf('apple') !== -1) {
    return true;
  } else {
    return false;
  }
});
// fruitsWithWordApple
// ['apple', 'pineapple']
```


Events
======

This library throw only one event ```change```.

How to use events? You can use array events like events in [Backbone Collection](http://backbonejs.org/#Collection).

```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.on('change', function(event) {
  // event
  // {
  //   "type": "push",
  //   "args": ['mongo'],
  //   "result": 4
  // }
  
  console.log('fruits list is changed.');
});

// fruits.events
// [{
//  "name": "change",
//  "handler": function() { ... }
// }]

fruits.push('mango');
// fruits list is changed.
// fruits
// ['apple', 'orange', 'pineapple', 'mango']
```

Events Handling and Triggering
==============================

***Notice:*** Traditional mutator ```arr[index] = value``` do not trigger event ```change```. Use method ```set(index, value)``` instead ```arr[index] = value```.

on(eventName, handler)
----------------------

Attach event handler.

Example:
```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.on('change', function(event) {
  // event
  // {
  //   "type": "push",
  //   "args": ['mango'],
  //   "result": 4
  // }
  
  console.log('fruits list is changed.');
});

fruits.push('mango');
```

trigger(eventName, args)
------------------------

Trigger some event.

```javascript
var fruits = new Arr('apple', 'orange', 'pineapple');

fruits.on('change', function(event) {
  console.log('fruits list is changed.');
});

fruits.trigger('change');
// fruits list is changed.
```
