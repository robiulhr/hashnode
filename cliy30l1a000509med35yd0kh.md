---
title: "How to Split a Number into an Array in JavaScript"
seoTitle: "How to Split a Number into an Array in JavaScript"
seoDescription: "There are scenarios where you might need to split a number into its digits and store them in an array When working with numbers in JavaScript. This can b..."
datePublished: Fri Jun 16 2023 04:40:44 GMT+0000 (Coordinated Universal Time)
cuid: cliy30l1a000509med35yd0kh
slug: how-to-split-a-number-into-an-array-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686838271650/a0bb8c5d-48ba-47e2-98aa-bfc62432a2fa.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686885346847/ad02035f-6294-429d-9269-458006e85d88.png
tags: tutorial, programming-blogs, javascript, web-development, tips-and-tricks

---

## Introduction

There are scenarios where you might need to split a number into its digits and store them in an array When working with numbers in JavaScript. This can be useful for tasks such as performing mathematical operations on each digit or manipulating the digits individually.

In this article, we will delve into various techniques for splitting a number into an array of digits using JavaScript. We will not only cover the fundamental approaches but also address important considerations such as handling negative numbers and float numbers.

By the end of this article, you will gain a comprehensive understanding of how to extract and organize the digits of a number effectively. Whether you're working with integers or float numbers, this article will equip you with the necessary knowledge and techniques to accomplish the task efficiently.

So, Let's get started!

## Different Ways to split numbers into Arrays

In the context of splitting numbers, there are two main approaches that we will explore in this article:

* Using string conversion
    
* Using math operations.
    

These approaches offer different ways to extract individual digits from a number and store them in an array.

By leveraging string conversion, we can convert the number into a string and iterate over its characters.

On the other hand, using math operations allows us to perform calculations to extract the digits.

Both approaches have their advantages and are suited for different scenarios.

Let's delve into each approach and explore its implementation in detail.

## Splitting a Number Using String Conversion

The most straightforward approach to splitting a number into an array is by converting it to a string and then iterating over each character to extract the digits.

![Splitting a Number Using String Conversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1686883927843/41a3924b-8c73-4610-b71c-135c7a12930c.webp align="center")

This technique involves converting the number to a string representation using methods like [`toString()`](https://www.w3schools.com/jsref/jsref_tostring_string.asp#:~:text=The%20toString()%20method%20is,it%20in%20your%20own%20code.) or the [`String()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/String) constructor. Once the number is converted to a string, we can access each character and extract the desired digits.

There are multiple techniques available to do that,

Let's explore some of these techniques to gain a better understanding of how to split a number into an array using string conversion.

### Split Number Using `for loop`

We can use a [`for loop`](https://www.freecodecamp.org/news/javascript-for-loops/) to iterate over each digit of the number and add it to an array after converting the number to a string.

Here's an example that demonstrates the usage of a for loop to split a number into an array:

```javascript
 function splitNumberUsingForLoop(number) {
   const digits = [];
   const numberString = number.toString(); // Convert the number to a string
   
   for (let i = 0; i < numberString.length; i++) {
     const digit = parseInt(numberString[i]); // Convert each character back to a number
     digits.push(digit); // Add the digit to the end of the array
   }
   
   return digits;
 }

 const number = 12345;
 const digits = splitNumberUsingForLoop(number);
 console.log(digits); // [1, 2, 3, 4, 5]
```

In the example above, we define a function called `splitNumberUsingForLoop` that takes a number as input. Inside the function, we initialize an empty array called digits to store the individual digits of the number. We convert the number to a string using the `toString()` method.

Next, we use a for loop to iterate over each character in the `numberString`. We convert each character back to a number using [`parseInt()`](https://www.scaler.com/topics/parseint-in-javascript/) and then push it to the digits array using the [`push()`](https://www.javascripttutorial.net/javascript-array-push/) method.

After the loop finishes, we return the digits array, which contains all the individual digits of the number.

Using a for loop gives us control over the iteration process and allows us to handle each digit individually. It provides flexibility in case we need to perform additional operations or validations during the iteration.

### Split Number Using `split()` Method

Another way to split a number into an array of digits in the string conversion approach is by using the [`split()`](https://www.javascripttutorial.net/javascript-string-split/) method after converting the number to a string.

Here's an example that demonstrates the usage of the split() method:

```javascript
const number = 12345;
const numberString = number.toString(); // Convert the number to a string
const digits = numberString.split(""); // Split the string into an array of individual characters

console.log(digits); // ["1", "2", "3", "4", "5"]
```

In the example above, we convert the number to a string using the `toString()` method. Then, we call the `split("")` method on the resulting string, passing an empty string as the separator. This splits the string into an array of individual characters, which represent the digits of the number.

By using the `split()` method, we can easily obtain an array of digits from a number. This approach is straightforward and can be useful when you specifically need the digit values as strings.

### Split Number Using Spread Operator

Another way to split a number into an array of digits is by using the [spread operator](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab) after converting the number to a string. The spread operator allows us to spread the characters of a string into individual elements of an array.

Here's an example that demonstrates the usage of the spread operator:

```javascript
const number = 12345;
const numberString = number.toString(); // Convert the number to a string
const digits = [...numberString]; // Spread the characters of the string into an array

console.log(digits); // ["1", "2", "3", "4", "5"]
```

In the example above, we convert the number to a string using the `toString()` method. Then, by using the spread operator \[`...`\], we spread the characters of the string into individual elements of an array. This results in an array where each element represents a digit of the number.

Using the spread operator provides a concise and readable way to split a number into an array of digits. It is particularly useful when you need to work with the digit values as strings and want to avoid using the `split()` method.

### Split Number Using `reduce()` or `map()` method

As you can see When using the `.split()` method or spread operator to split a number into an array of digits, the resulting array will contain string values as the elements.

However, if you prefer the elements to be numbers instead of strings, you can combine this approach with the [`.reduce()`](https://www.freecodecamp.org/news/reduce-f47a7da511a9/) or [`.map()`](https://www.freecodecamp.org/news/javascript-map-how-to-use-the-js-map-function-array-method/) method.

Here's an example using the `.reduce()` method:

```javascript
const number = 12345;
const numberString = number.toString(); // Convert the number to a string
const digits = numberString.split('').reduce((acc, curr) => {
  acc.push(parseInt(curr)); // Convert each character back to a number
  return acc;
}, []);

console.log(digits); // [1, 2, 3, 4, 5]
```

In this example, we first convert the number to a string using the `.toString()` method. Then, we split the string into an array of individual characters using `.split('')`.

By applying the `.reduce()` method, we iterate over each character and use `parseInt()` to convert it back to a number. The resulting array contain the number values instead of strings.

Similarly, you can achieve the same result using the `.map()` method:

```javascript
const number = 12345;
const numberString = number.toString(); // Convert the number to a string
const digits = [...numberString].map((digit) => parseInt(digit));

console.log(digits); // [1, 2, 3, 4, 5]
```

In this example, we convert the number to a string using the `.toString()` method. Then, by using the spread operator, we convert the string into an array of individual characters.

Finally, we apply the `.map()` method to iterate over each character and use `parseInt()` to convert it back to a number. The resulting array contains the number values extracted from the original number.

### Split Number Using Array.from() Method

We can use [`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) method to do that, This method creates a new array instance from an array-like or iterable object, allowing us to generate an array of digits from a number. To split a number using the `Array.from()` method, we pass the string as the first argument to `Array.from()` after converting the number to a string.

Additionally, we can provide a mapping function as the second argument to convert each character to a numeric digit.

Here's an example that demonstrates the usage of the `Array.from()` method:

```javascript
const number = 12345;
const numberString = number.toString(); // Convert the number to a string
const digits = Array.from(numberString, Number); // Create an array of digits

console.log(digits); // [1, 2, 3, 4, 5]
```

In the example above, we convert the number to a string using the `toString()` method. Then, we pass the string and the Number function as arguments to `Array.from()`. The Number function is used as a mapping function to convert each character of the string to a numeric digit.

Using the `Array.from()` method provides a flexible approach to splitting a number into an array of digits. It allows us to customize the mapping function if needed and provides a clean and concise solution for the task.

## Splitting a Number Using Math Operations

Another approach to splitting a number is by Using Math Operations which involves using mathematical operations such as modulus and division.

![Splitting a Number Using Math Operations](https://cdn.hashnode.com/res/hashnode/image/upload/v1686883979391/233c88ea-f65b-4ef9-81e7-af1e2ebb1ecc.webp align="center")

By leveraging the [Remainder or modulus operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Remainder) (`%`) and division, we can isolate each digit and add it to an array. This method is more suitable when you require precise numeric calculations along with digit extraction.

There are several ways to implement this approach.

Let's explore the most popular two of them:

### Split Number Using `while Loop`

One way to split a number using math operations is by utilizing a [`while loop`](https://www.w3schools.com/js/js_loop_while.asp).

Here's an example implementation:

```javascript
function splitNumberUsingWhileLoop(number) {
  const digits = [];
  let tempNumber = number;

  while (tempNumber > 0) {
    const digit = tempNumber % 10;
    digits.unshift(digit);
    tempNumber = Math.floor(tempNumber / 10);
  }

  return digits;
}

const number = 12345;
const digits = splitNumberUsingWhileLoop(number);
console.log(digits); // [1, 2, 3, 4, 5]
```

In this implementation, we start with an empty digits array. The `tempNumber` variable is initialized with the input number. The `while loop` runs as long as `tempNumber` is greater than `0`. In each iteration, we extract the last digit of tempNumber using the modulus operator (`%`) and add it to the beginning of the digits array using the `unshift()` method.

Then, we update `tempNumber` by dividing it by 10 and using [`Math.floor()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) to remove the last digit. This process continues until `tempNumber` becomes `0`, indicating that all digits have been extracted. Finally, we return the `digits` array.

### Split Number Using Recursion

Recursion is another way to split a number using math operations. It involves breaking down a number into its digits by utilizing a recursive function. Each recursive call processes a portion of the number, gradually extracting the digits until the base case is reached.

Here's an example implementation:

```javascript
function splitNumberRecursive(number) {
  if (number < 10) {
    return [number]; // Base case: return the single digit
  }

  const lastDigit = number % 10; // Extract the last digit
  const remainingNumber = Math.floor(number / 10); // Remove the last digit

  return [...splitNumberRecursive(remainingNumber), lastDigit]; // Concatenate the recursive result with the last digit
}

const number = 12345;
const digits = splitNumberRecursive(number);
console.log(digits); // [1, 2, 3, 4, 5]
```

In this recursive implementation, the function checks if the number is less than `10`, which indicates that we have reached the base case of a single digit. If the base case is met, the function returns an array containing that single digit.

Otherwise, it extracts the last digit using the modulus operator (`%`) and removes the last digit using division and `Math.floor()`. The function then recursively calls itself with the remaining number and concatenates the recursive result with the last digit.

## Handling Negative Numbers

So far we have discussed different approaches for splitting a number but Handling negative numbers when splitting them requires special attention to ensure accurate results. If we don't handle negative numbers separately, it can introduce complexity into our code.

Let's explore how we can handle negative numbers:

### Handling Negative Numbers in String Conversion

When using string conversion to split numbers, we can incorporate handling for negative numbers during the conversion process.

Here's the updated code that considers negative numbers in for loop approach that we talked about earlier:

```javascript
function splitNumberUsingForLoop(number) {
  const digits = [];
  const numberString = Math.abs(number).toString(); // Convert the absolute value of the number to a string

  for (let i = 0; i < numberString.length; i++) {
    const digit = parseInt(numberString[i]); // Convert each character back to a number
    digits.push(digit); // Add the digit to the end of the array
  }

  if (number < 0) {
    digits[0] = -digits[0]; // Modify the first digit to include the negative sign
  }

  return digits;
}

const number = -12345;
const digits = splitNumberUsingForLoop(number);
console.log(digits); // [-1, 2, 3, 4, 5]
```

In this updated code, we first convert the absolute value of the number to a string using [`Math.abs()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs) to ensure we're working with positive numbers. The rest of the logic remains the same, where each character is converted back to a number and added to the digits array.

After the loop, we check if the original number is negative (number &lt; `0`). If it is, we modify the first digit in the digits array to include the negative sign. This way, the resulting array represents the correct split digits of the negative number.

> Note: Here we have used the `for loop` approach only but you can do the same with other approaches too.

### Handling Negative Numbers in Math Operations

When splitting numbers using Math Operations, we can also incorporate handling for negative numbers within the code. By making a simple adjustment, we can ensure accurate results even when dealing with negative values.

Here's the updated code for handling negative numbers using math operations:

```javascript
function splitNumberUsingWhileLoop(number) {
  const digits = [];
  let tempNumber = Math.abs(number);

  while (tempNumber > 0) {
    const digit = tempNumber % 10;
    digits.unshift(digit);
    tempNumber = Math.floor(tempNumber / 10);
  }

  if (number < 0) {
    digits[0] = -digits[0]; // Adjust the sign of the first digit for negative numbers
  }

  return digits;
}

const number = -12345;
const digits = splitNumberUsingWhileLoop(number);
console.log(digits); // [-1, 2, 3, 4, 5]
```

In this updated code, we first obtain the absolute value of the number using `Math.abs()` and assign it to the `tempNumber` variable. Then, we perform the splitting process as before using the `while loop`. After the loop, we add an additional check to adjust the sign of the first digit if the original number is negative. This ensures that negative numbers are correctly handled during the splitting operation.

> Note: Here we have used the `while loop` approach only but you can do the same with the recursion approach too.

## Handling Float Numbers

Just like negative numbers, When it comes to splitting float numbers, additional considerations are necessary to handle both the integer and fractional parts accurately. Let's explore techniques to split float numbers into their integer and fractional components:

### Handling Float Numbers in String Conversion

To split float numbers using string conversion, we can leverage the same approach as discussed earlier but need to do some extra stuff to handle the floating point.

First, we convert the float number to a string and then split it based on the decimal point. The resulting array will contain two elements: the integer part and the fractional part.

Here's the updated code for the split approach:

```javascript
function splitFloatNumberUsingStringConversion(floatNumber) {
  const numberString = floatNumber.toString();
  const [integerPart, fractionalPart] = numberString.split(".");

  const integerDigits = integerPart.split("").map(Number);
  const fractionalDigits = fractionalPart ? fractionalPart.split("").map(Number) : [];

  return { integerDigits, fractionalDigits };
}

// Example usage
const floatNumber = 12.345;
const { integerDigits, fractionalDigits } = splitFloatNumberUsingStringConversion(floatNumber);
console.log(integerDigits);     // [1, 2]
console.log(fractionalDigits);  // [3, 4, 5]
```

In this code, the `splitFloatNumberUsingStringConversion` function takes a floating-point number and converts it to a string. It then splits the string into separate parts for the integer and fractional portions using the dot (`.`) as the delimiter.

The integer part is converted to an array of digits by splitting the string and mapping each character to a number using the map function. The fractional part is also converted to an array of digits in a similar way. If there is no fractional part, an empty array is returned for `fractionalDigits`.

Finally, the function returns an object containing the `integerDigits` and `fractionalDigits` arrays. These arrays can be accessed separately and used as needed. In the provided example, integerDigits contains `[1, 2]` and fractionalDigits contains `[3, 4, 5]`, representing the integer and fractional parts of the original floating-point number, respectively.

> Note: We have not covered the handling of float numbers in the math operation approach to keep things simple. Float numbers can introduce precision limitations and rounding errors in JavaScript. To handle float numbers accurately, additional steps and considerations are required. In this article, we have focused on the handling of whole numbers to provide a straightforward explanation.

## Conclusion

In this article, we explored various techniques for splitting a number into an array in JavaScript. Whether you prefer string conversion or mathematical operations each approach offers its advantages and can be applied based on your specific requirements.

By mastering the art of splitting numbers, you'll have the flexibility to handle numerical data effectively and perform various calculations with ease.

Remember to consider factors such as decimal numbers, negative numbers, and performance optimizations when implementing these techniques. With a solid understanding of splitting numbers in JavaScript, you'll be well-equipped to tackle complex numeric tasks in your projects.

Happy coding :)