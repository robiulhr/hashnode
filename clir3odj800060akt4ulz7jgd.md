---
title: "How to Rename an Object Key in JavaScript"
seoTitle: "How to Rename an Object Key in JavaScript"
seoDescription: "You may encounter scenarios where you need to rename an object key When working with objects in JavaScript. Renaming object keys can help to maintain..."
datePublished: Sun Jun 11 2023 07:24:50 GMT+0000 (Coordinated Universal Time)
cuid: clir3odj800060akt4ulz7jgd
slug: how-to-rename-an-object-key-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686377375166/369fbd1e-6091-4ff4-8357-2fb1feeb922f.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686384101862/7423e98f-4ad1-4a4e-92f9-8ac8783c310f.webp
tags: tutorial, programming-blogs, javascript, web-development, tips

---

## Introduction

You may encounter scenarios where you need to rename an object key When working with objects in JavaScript. Renaming object keys can help to maintain consistency, enhance code readability, or align with specific naming conventions.

In this blog post, we will delve into different techniques and approaches to effectively rename object keys in JavaScript. We'll cover both mutable and immutable methods, including manual approaches using [`Object.assign()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign), [`Object.defineProperty()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty), object destructuring, property assignment, and more.

Additionally, we'll discover the benefits of leveraging external libraries like [Lodash](https://lodash.com/) that provide specialized functions for renaming object keys.

By the end of this article, you'll have a solid understanding of how to tackle key renaming tasks in JavaScript, empowering you to write more concise and organized code.

So, Let's start!

## **Prerequisites**

Before diving into the concept of renaming object keys in JavaScript, it's important to have a basic understanding of the language and its fundamental concepts like [variables](https://robiul.dev/javascript-variables-beginner-thinking), functions, and basic control flow (such as if statements and [loops](https://robiul.dev/javascript-loop-best-practices-for-optimal-performance)).

If you are new to JavaScript or need a refresher, there are several online resources available, such as [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript), [W3Schools](https://www.w3schools.com/js/), and [freeCodeCamp](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/), that offer comprehensive tutorials and guides.

In addition to these resources, two highly recommended books for beginners in JavaScript are:

* [Head First JavaScript Programming: A Brain-Friendly Guide](https://amzn.to/3Clu7un)
    
* [JavaScript: The Definitive Guide: Master the World's Most-Used Programming Language](https://amzn.to/43VPa2B)
    

These books will provide you with a solid foundation in JavaScript programming, allowing you to confidently explore the techniques and concepts discussed in this article.

By having a strong grasp of JavaScript fundamentals, you'll be well-prepared to understand the various methods and approaches for renaming object keys in JavaScript.

## Immutable Object Approach

In JavaScript, objects are mutable, meaning you can modify their properties directly. However, when it comes to renaming object keys, you may prefer to maintain immutability and create a new object with the updated key.

![Immutable Object Approach](https://cdn.hashnode.com/res/hashnode/image/upload/v1686465314171/f1beca2c-9c13-4420-a556-3642e50bd249.webp align="center")

To achieve this, you can follow the immutable object approach, which involves creating a new object with the desired key name while preserving the other properties. This approach ensures that the original object remains unchanged.

By employing the immutable object approach, you ensure that the original object remains intact and create a new object with the desired key renaming.

There are a few commonly used techniques for achieving this.

Let's explore them:

### Using Object Destructuring and Property Assignment:

One way to rename an object key in an immutable approach is by utilizing [object destructuring](https://medium.com/javascript-in-plain-english/level-up-your-code-in-5-ways-using-destructuring-assignment-1e4cbbe96a99) and property assignment. This technique involves extracting the value associated with the existing key and assigning it to a new key without altering the original object.

Here's an example:

```javascript
const myObject = { oldKey: 'value' };  

// Renaming the key from 'oldKey' to 'newKey' 
const { oldKey: newKey, ...rest } = myObject; 
const updatedObject = { newKey, ...rest };
  
console.log(updatedObject); // { newKey: 'value' }
```

In the above example, we start with an object `myObject` that has a key called `oldKey` with a corresponding value. By using object destructuring, we create a new variable `newKey` and assign it the value of `oldKey`. The rest of the properties in the object are collected using the spread operator `...rest`.

This ensures that all other properties of the original object are preserved in the `updatedObject`.

Finally, we create a new object `updatedObject` with the renamed key `newKey` and include the remaining properties from `myObject`.

> Note: It's important to note that this method does not modify the original object `myObject`. Instead, it creates a new object `updatedObject` with the desired key renaming. The original object `myObject` remains unchanged and can still be accessed separately.

Using object destructuring and property assignment provides a concise and elegant way to rename object keys while maintaining the integrity of the original object. This approach can be especially useful when you want to create a modified version of an object without altering the original data.

### Creating a New Object with Renamed Keys

Another approach to renaming object keys while preserving the original object is by creating a new object with the renamed keys.

```javascript
const myObject = { oldKey: 'value' };  

// Creating a new object with renamed key 
const updatedObject = { newKey: myObject.oldKey };  

console.log(updatedObject); // { newKey: 'value' }
```

In the above example, we directly create a new object `updatedObject` with the desired key `newKey` and assign it the corresponding value from the original object `myObject`.

This allows us to achieve the renaming effect while keeping the original object intact. Unlike the object destructuring approach, which extracts all properties and creates a new object, this method selectively picks the specific key-value pair from the original object and assigns it to a new key in the updated object.

This approach can be useful when you only need to rename a few specific keys and want to avoid creating a duplicate object with all properties. It provides a straightforward and concise way to achieve key renaming without modifying the original object.

### Using `Object.assign()` method

Another method to rename an object key while not modifying the original object is by using the `Object.assign()` method. This method allows you to copy the properties of one or more source objects to a target object.

For example, you can create a new object and assign the desired key-value pair using `Object.assign()`:

```javascript
const myObject = { oldKey: 'value' };

// Creating a new object with renamed key using Object.assign()
const updatedObject = Object.assign({}, {
    newKey: myObject.oldKey
 });

console.log(updatedObject); // { newKey: 'value' }
```

In the above example, we use `Object.assign()` to create a new object by merging an empty target object (`{}`) with the properties of the `myObject` and an additional key-value pair (`{ newKey: myObject.oldKey }`).

This allows us to achieve key renaming without modifying the original object.

### Using `Object.defineProperty()` method

Another approach to renaming object keys while maintaining immutability is by using the `Object.defineProperty()` method. This method allows you to define or modify the properties of an object, including renaming keys.

Here's an example:

```javascript
const myObject = { oldKey: 'value' };

// Creating a new object with the renamed key using Object.defineProperty()
const updatedObject = Object.defineProperty(
  {},
  'newKey',
  Object.getOwnPropertyDescriptor(myObject, 'oldKey')
);

console.log(updatedObject); // { newKey: 'value' }
```

In the above example, we create a new object `updatedObject` and use `Object.defineProperty()` to define the property `newKey` based on the descriptor of the `oldKey` from the original object. This creates a new object with the desired key renamed while preserving the associated value.

By utilizing `Object.defineProperty()`, we can achieve key renaming in an immutable manner by creating a new object with the renamed key, leaving the original object unchanged.

## Modifying the Original Object

If you are open to modifying the original object, you can directly rename the key within the existing object by deleting the old key and assigning a new key-value pair. This approach allows you to update the object in place and achieve the desired key renaming effect.

![Modifying the Original Object](https://cdn.hashnode.com/res/hashnode/image/upload/v1686465361907/95b0b39a-b945-4153-8874-0e372277616c.webp align="center")

We can achieve this by using `delete` operator or combining other methods with [`delete` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete).

Let's explore them:

> Note: It's important to note that this approach directly modifies the original object. If you have any dependencies or references to the original key, they will be impacted by this renaming operation.
> 
> Therefore, consider this method when it is acceptable and desired to update the object in place.

### Using `delete` operator

Using the `delete` operator is the most commonly used approach to rename object keys by modifying the original object in Javascript.

Here's an example:

```javascript
const myObject = { oldKey: 'value' };  

// Renaming the key within the original object 
myObject.newKey = myObject.oldKey; 
delete myObject.oldKey;  

console.log(myObject); // { newKey: 'value' }
```

In the above example, we start with an object `myObject` that has a key called `oldKey` with a corresponding value. To rename the key, we first assign the value of `myObject.oldKey` to a new key called newKey within the same object. This effectively renames the key while preserving the associated value.

Next, using the delete operator, we remove the `oldKey` from the object, ensuring that only the new key remains. As a result, the object is modified, and we obtain the desired key renaming within the original object itself.

You can also use bracket notation to assign the new value and delete the old one:

```javascript
const myObject = { oldKey: 'value' };  

// Renaming the key within the original object 
myObject["newKey"] = myObject["oldKey"]; 
delete myObject["oldKey"];  

console.log(myObject); // { newKey: 'value' }
```

### Combining Other methods with `delete` operator

While renaming an object key Modifying the Original Object approach typically refers to using the delete operator, it is worth noting that you can achieve the same effect by combining other techniques like `Object.assign()` or `Object.defineProperty()` with the `delete` operator.

Here's an example that demonstrates the combination of techniques:

```javascript
const myObject = { oldKey: 'value' };

// Renaming the key using Object.assign() and delete operator
Object.assign(myObject, { newKey: myObject.oldKey });
delete myObject.oldKey;

console.log(myObject); // { newKey: 'value' }
```

In the above example, we first use `Object.assign()` to assign a new key-value pair to the original object, effectively renaming the key. Then, we use the delete operator to remove the old key from the object.

By combining these techniques, we achieve the desired key renaming effect while modifying the original object.

It's important to consider the implications of combining these techniques. Ensure that the properties you are assigning using `Object.assign()` does not conflict with existing keys in the object.

By combining different techniques, you can customize the key renaming process and choose the most suitable approach for your specific use case.

## Using a Library or Utility Function

In addition to the manual approaches discussed earlier, you can leverage existing JavaScript libraries or utility functions specifically designed for renaming object keys. These libraries provide convenient methods that simplify the process and offer additional functionalities.

![Using a Library or Utility Function](https://cdn.hashnode.com/res/hashnode/image/upload/v1686465402589/1db98f0a-fd33-4b8c-a870-0235aface8b0.webp align="center")

One such popular library is `Lodash`, which provides a rich set of utility functions for JavaScript. Lodash includes a renameKeys function that allows you to rename object keys easily.

> Note: The approach mentioned in this section requires the lodash.js library, which is not available in standard JavaScript. To use this method, you need to install the `lodash` library using the following command:
> 
> ```bash
> npm i --save lodash
> ```
> 
> Please note that this command assumes you have npm (Node Package Manager) installed and configured in your development environment. Installing the `lodash` library will provide you with additional functionality for renaming object keys in JavaScript.

Here's an example of how you can use `Lodash`'s `renameKeys` function:

```javascript
const _ = require('lodash');  
const myObject = { oldKey: 'value' };  

// Renaming the key using Lodash 
const updatedObject = _.renameKeys(myObject, { oldKey: 'newKey' });  

console.log(updatedObject); // { newKey: 'value' }
```

In the above example, we start by importing the `Lodash` library using the `require` statement. We have an object `myObject` with a key called `oldKey` and its corresponding value.

By using Lodash's `renameKeys` function, we pass in the `myObject` and an object specifying the key mapping to perform the renaming. In this case, we want to rename the oldKey to newKey.

The `renameKeys` function performs the key renaming operation and returns a new object updatedObject with the renamed key.

By utilizing a library like `Lodash`, you can benefit from well-tested and optimized code, reducing the amount of custom code you need to write and potentially improving performance.

## Rename multiple keys using `map()` method

So far, we have explored various approaches to renaming object keys in javascript. However, there may be situations where you need to rename multiple keys simultaneously.

In such cases, you can leverage the [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) method in combination with any of the techniques discussed in this article.

The `map()` method allows you to iterate over the keys of an object and perform a transformation operation on each key-value pair. By utilizing this method, you can easily rename multiple keys in one go.

Here's an example that demonstrates the use of the `map()` method for renaming multiple keys:

```javascript
const myObject = {
  oldKey1: 'value1',
  oldKey2: 'value2',
  oldKey3: 'value3'
};

const keyMap = {
  oldKey1: 'newKey1',
  oldKey2: 'newKey2',
  oldKey3: 'newKey3'
};

const updatedObject = Object.fromEntries(
  Object.entries(myObject).map(([key, value]) => [keyMap[key] || key, value])
);

console.log(updatedObject);
/*
{
  newKey1: 'value1',
  newKey2: 'value2',
  newKey3: 'value3'
}
*/
```

In the above example, we define a `keyMap` object that maps the old keys to their corresponding new keys. We then use the `map()` method in combination with `Object.entries()` to iterate over the object's key-value pairs.

Within the `map()` callback, we check if a key exists in the keyMap object and use the mapped new key if available, or keep the original key as is.

Finally, we use [`Object.fromEntries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries) to convert the updated key-value pairs back into an object.

By using the `map()` method, you can efficiently rename multiple keys in an object with ease. This approach provides flexibility and allows for more complex key renaming scenarios.

## Deep Object Key Renaming

In some cases, you may need to rename keys that are nested within nested objects or arrays. The techniques mentioned earlier can be extended to handle deep object key renaming.

> Note: This section covers an advanced technique for renaming keys within deeply nested objects. If you find it challenging or are not familiar with nested data structures in JavaScript, feel free to skip this section.

One approach is to use recursion to traverse through the object and rename keys at each level.

Here's an example implementation:

```javascript
function renameKeysDeep(obj, keyMap) {
   if (typeof obj !== 'object' || obj === null) {
     return obj;
   }

   if (Array.isArray(obj)) {
     return obj.map((item) => renameKeysDeep(item, keyMap));
   }

  const renamedObj = {};

  for (const key in obj) {
     if (obj.hasOwnProperty(key)) {
       const newKey = keyMap[key] || key;
       renamedObj[newKey] = renameKeysDeep(obj[key], keyMap);
     }
   }
   return renamedObj; 
}  

const myObject = {
   id: 1,
   info: {
     name: 'John',
     age: 30,
     address: {
       street: '123 Main St',
       city: 'New York',
     },
   },
 };  

const updatedObject = renameKeysDeep(myObject, {
   id: 'userId',
   name: 'fullName',
   street: 'location.street',
 });  

console.log(updatedObject); 

/* 
{
   userId: 1,
   info: {
     fullName: 'John',
     age: 30,
     address: {
       location.street: '123 Main St',
       city: 'New York',
     },
   },
 } 
*/
```

In this provided example, the `renameKeysDeep` function is employed to recursively traverse the object and rename keys based on the provided `keyMap` object.

The function intelligently handles nested objects and arrays, ensuring that keys are appropriately renamed throughout the data structure.

By implementing deep object key renaming, you gain the flexibility to work with intricate data structures and maintain consistent key renaming across all levels of nesting.

This technique proves valuable when you encounter complex objects that require key modifications within deeply nested hierarchies.

## Conclusion

In this blog post, we explored various techniques for renaming object keys in JavaScript. We discussed the Immutable Object Approach, Modifying the Original Object with Renamed Keys, Using a Library or Utility Function, and Deep Object Key Renaming.

These approaches provide different ways to achieve key renaming based on factors such as immutability, in-place modification, external library usage, renaming multiple keys, and handling nested objects.

By understanding these techniques, you now have the tools to efficiently rename object keys according to your specific needs. Choose the approach that suits your project and enjoy the benefits of consistent and readable code.

Happy coding :)