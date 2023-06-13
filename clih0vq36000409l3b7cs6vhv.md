---
title: "How to Check if a String is Empty in JavaScript"
seoTitle: "How to Check if a String is Empty in JavaScript"
seoDescription: "It's crucial to have reliable techniques to check if a string is empty in JavaScript, whether you're validating user input, processing data, or ..."
datePublished: Sun Jun 04 2023 06:08:53 GMT+0000 (Coordinated Universal Time)
cuid: clih0vq36000409l3b7cs6vhv
slug: how-to-check-if-a-string-is-empty-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685714395868/e51df285-5fa2-4a34-ba88-4314d1ab3742.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685858583004/356ebf00-afd5-4c25-a875-23ded513e408.webp
tags: tutorial, programming-blogs, javascript, web-development, tips

---

## Introduction

Working with strings is a common task in JavaScript development. Whether you're validating user input, processing data, or implementing string manipulation operations, it's important to have robust techniques to check if a string is empty in javascript.

In this blog post, we will dive into various approaches to check if a string is empty in JavaScript. We'll cover methods that not only detect an empty string but also handle scenarios where the string may contain only whitespace characters, or it may be `null` or `undefined`.

By familiarizing yourself with these techniques, you'll gain the knowledge and tools necessary to handle empty string scenarios effectively in your JavaScript code.

Let's get started!

## Why do we need to check Empty string

Before we jump into different ways of checking if a string is empty or not, let's take a moment to understand why it's important. At first, it may seem like a small detail, but there are good reasons why we need to pay attention to empty strings.

By understanding the reason, we can see how this seemingly simple task can have a big impact on our code.

To illustrate the importance of checking for an empty string, let's consider a simple example.

Imagine a scenario where you have a search feature on your website that allows users to input a search query. Let's say the search functionality uses JavaScript to process the query and display the search results.

Here's a code example without checking for an empty string:

```javascript
// Example: Search functionality without checking for an empty string 
let performSearch = function(){
    // code here
}
let searchQuery = document.getElementById('search input').value 
// Process the search query and display the results 
performSearch(searchQuery)
```

In this code, the `searchQuery` variable is assigned the value of the user's input from an HTML input field with the ID `searchInput`. However, this code doesn't include any validation to check if the user has actually entered a search query or left the field empty.

The problem arises when a user submits the form without entering any search query. Without checking for an empty string, the code will proceed to process the empty search query. This can lead to unexpected behavior, such as displaying incorrect or irrelevant search results or throwing errors in the search functionality.

By not checking for an empty string in the search functionality, if the user submits the form without entering any search query, the code will still proceed to execute the search logic.

In this case, it will log an error message indicating an empty search query. This helps to highlight the unexpected behavior that can occur when empty input is not properly validated.

To address this issue, it is important to check if the search query is empty before proceeding with the search functionality.

## Method 1: Using the Length Property

The simplest way of checking if a string is empty in JavaScript is the [`length`](https://www.w3schools.com/jsref/jsref_length_string.asp) property. By comparing the length of a string to zero, we can determine if it is empty or not.

```javascript
let myStr = ''

if (myStr.length === 0) {
  console.log('This is a javascript empty string!')
}
```

However, this approach will not handle cases where the string contains only whitespace characters.

To overcome this, we can use the `trim()` method to remove the leading and trailing whitespace before checking the length.

Consider the following code snippet:

```javascript
let myStr = ' ';

if (myStr.trim().length === 0) {
  console.log('This is a javascript empty string!');
} else {
  console.log('This is NOT a javascript empty string!');
}
```

In this case, the initial check would erroneously classify the string as non-empty due to the presence of whitespace.

However, by applying the [`trim()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim) method, we ensure that whitespace is eliminated before checking the length, and correctly identifying an empty string.

It's important to note that the `length` property does not work for [`null`](https://www.programiz.com/javascript/null-undefined) or [`undefined`](https://www.programiz.com/javascript/null-undefined) values, and attempting to access the length property of a `null` or `undefined` value will throw an error.

![the length property does not work for null or undefined values](https://cdn.hashnode.com/res/hashnode/image/upload/v1685724626793/74b2095a-d063-4a1e-a82a-35899cdef507.webp align="center")

To handle these, we can add additional conditions to check if the value is of a type string before performing the length check.

For instance:

```javascript
let myStr = null;

if (typeof myStr === 'string' && myStr.trim().length === 0) {
  console.log('This is a javascript empty string!');
}
```

This code first verifies that the value is a string using the `typeof` operator before applying the `trim()` method and checking the `length`. This approach prevents errors when dealing with `null` or `undefined` values.

To handle all of these `null`, `undefined`, and empty string at the same time, we can combine the conditions using the logical (`||`) [OR operator](https://www.geeksforgeeks.org/or-logical-operator-in-javascript/):

```javascript
let myStr = null;

if (myStr === null || myStr === undefined || myStr.trim().length === 0) {
  console.log('This is a javascript empty string!');
} else {
  console.log('This is not a javascript empty string!');
}
```

By considering all these scenarios, we can accurately determine whether a string is empty or not, ensuring proper handling and avoiding potential issues in our code.

## Method 2: comparing to a string

Another approach to checking if a string is empty is by comparing it to an empty string.

Here's an example:

```javascript
let myStr = "";

if (myStr === "") {
  console.log("This is a javascript empty string!");
}
```

However, similar to the previous method, this approach does not consider strings that contain only whitespace characters. To treat a string containing only whitespace as empty, we can use the `trim()` method before comparing it to an empty string.

Here's an example function that checks if a string is empty, considering whitespace characters:

```javascript
function checkIfEmpty(str) {
  if (str.trim() === '') {
    console.log('String is empty string');
  } else {
    console.log('String is NOT empty string');
  }
}

const str1 = 'not empty';
const str2 = '';      // empty
const str3 = ' ';     // contains only whitespace

checkIfEmpty(str1);   // outputs: String is NOT empty
checkIfEmpty(str2);   // outputs: String is empty
checkIfEmpty(str3);   // outputs: String is empty
```

In the `checkIfEmpty` function, we call the `trim()` method on the string to remove any leading or trailing whitespace. Then, we compare the resulting trimmed string with an empty string to determine if it's empty or not.

Using the `trim()` method ensures that strings containing only whitespace characters are treated as empty. It removes all whitespace from the beginning and end of the string, returning a new string without modifying the original.

> Note: Trimming a string is particularly useful when validating required fields in a form, as it helps ensure that the user entered actual data instead of just whitespace.

## Method 3: Using the `!` Operator

Javascript treats empty strings as falsy values, which means they evaluate to `false` in a boolean context. We can take advantage of this behavior to check if a string is empty using the negation operator `(!)`.

Here's an example:

```javascript
function isEmptyString(str) {
  return !str;
}
```

In this example, the `isEmptyString` function takes a string as an argument and returns `true` if the string is empty, and `false` otherwise. By using the negation operator `!`, we are essentially checking if the string is falsy, which includes empty strings.

However, like the previous methods, this approach does not consider strings that contain only whitespace characters. To handle whitespace characters, we can combine this approach with the `trim()` method.

Here's an example:

```javascript
function checkIfEmpty(str) {
  if (!str.trim()) {
    console.log('String is empty');
  } else {
    console.log('String is NOT empty');
  }
}

const str1 = 'not empty';
const str2 = '';      // empty
const str3 = ' ';     // contains only whitespace

checkIfEmpty(str1);   // outputs: String is NOT empty
checkIfEmpty(str2);   // outputs: String is empty
checkIfEmpty(str3);   // outputs: String is empty
```

In the `checkIfEmpty` function, we call the `trim()` method on the string to remove leading and trailing whitespace. Then, we compare the trimmed string with an empty string to determine if it's empty or not.

The `trim()` method removes all whitespace from the beginning and end of a string and returns a new string, without modifying the original. This allows us to accurately handle strings with whitespace characters.

It's important to note that checking for an empty string using the negation operator or combining it with `trim()` will not handle null and undefined values. If you also need to handle null and undefined, you can modify the condition as follows:

```javascript
javascriptCopy codefunction checkIfEmpty(str) {
  if (!str || str.trim() === '') {
    console.log('String is empty');
  } else {
    console.log('String is NOT empty');
  }
}
```

In the above code, the condition `!str` checks if the `str` variable is `falsy` (`null`, `undefined`, an empty string, or a `0`). If it is, the code inside the `if` block will be executed, indicating that the string is empty.

By incorporating these checks, we ensure proper handling of empty strings, including those with whitespace characters, null values, and undefined variables, in our JavaScript code.

## Method 4: Using the Nullish Coalescing Operator (`??`)

Until now, we have explored three ways to check for an empty string. However, there is an advanced approach introduced in ECMAScript 2020 that can help reduce the amount of code needed.

The [nullish coalescing operator](https://javascript.info/nullish-coalescing-operator) (`??`) provides a concise way to check if a string is empty or bullish:

```javascript
function isEmptyString(str) {
  return (str ?? '') === '';
}
```

In the code above, the nullish coalescing operator (`??`) checks if the value of `str` is either `null` or `undefined`. If it is, the operator returns an empty string `''`. We then compare the result with an empty string `''` to determine if the string is empty or nullish.

By using the nullish coalescing operator, we can handle the scenario where the string is either `null` or `undefined`.

Additionally, we can leverage the [optional chaining](https://www.freecodecamp.org/news/javascript-optional-chaining/) (`?.`) operator to handle `null` and `undefined` values:

```javascript
const str = ' ';

if (str?.trim()) {
  console.log('The string is NOT empty');
} else {
  console.log('The string is empty');
}
```

The optional chaining operator (`?.`) short-circuits and returns `undefined` if the value to the left is nullish (`null` or `undefined`). This allows us to handle cases where the string variable holds an `undefined` value:

```javascript
const str = undefined;

if (str?.trim()) {
  console.log('The string is NOT empty');
} else {
  console.log('The string is empty');
}
```

Instead of encountering an error when trying to call the `trim()` method on an `undefined` value, the optional chaining operator prevents the error by returning `undefined`.

Using the nullish coalescing operator and optional chaining operator can simplify your code and handle `null`, `undefined`, and empty string scenarios more effectively.

## Value is NOT an empty string, undefined or null

Previously, we learned how to check if a string is empty, null, or undefined. Now, let's explore how to check if a string is not an empty string, undefined, or null using a similar approach.

To determine if a value is not an empty string, `undefined`, or `null`, you can use the logical AND (`&&`) operator in JavaScript. This approach ensures that all conditions must be met for the if block to be executed.

Let's break down the code:

```javascript
const str = 'bobbyhadz.com';

if (typeof str !== 'undefined' && str !== null && str.trim() !== '') {
  console.log('The value is NOT undefined, null, or an empty string');
} else {
  console.log('The value is undefined, null, or an empty string');
}
```

In the code above, we perform the following checks:

1. First, we use `typeof` to check if the variable `str` is not of type `undefined`. This condition prevents the code from throwing an error if `str` has not been declared or defined.
    
2. Next, we check if `str` is not `null`. The null value represents the intentional absence of any object value. In javascript, By checking whether the string is `null` or empty, we ensure that the variable has a valid value.
    
3. Finally, we verify that `str.trim()` is not an empty string. An empty string has no characters and is represented by two quotation marks with nothing in between.
    

By combining these conditions with the logical AND operator (`&&`), we ensure that all of them must evaluate to `true` for the if block to be executed. If any of the conditions is not met, the else block runs, indicating that the value is either `undefined`, `null`, or an empty string.

Using this approach provides a comprehensive check to determine if a value has valid content, helping you avoid unexpected behavior or errors in your code.

## Conclusion

In this blog post, we have explored various techniques to check for empty, `null`, or `undefined` strings in JavaScript. By using methods such as length comparison, string comparison, negation operator (`!`), and nullish coalescing operator (`??`), we can effectively handle these scenarios.

By incorporating these techniques into your code, you can ensure the reliability and stability of your JavaScript applications. Remember to practice and experiment with these methods to deepen your understanding and proficiency.

Continuously refining your skills will make you a more adept JavaScript developer, capable of leveraging these techniques to enhance the functionality of your applications.

Keep exploring and enjoy the journey of mastering JavaScript!

## **Resources**

* https://www.freecodecamp.org/news/javascript-check-empty-string-checking-null-or-empty-in-js/
    
* https://bobbyhadz.com/blog/javascript-check-if-string-is-empty