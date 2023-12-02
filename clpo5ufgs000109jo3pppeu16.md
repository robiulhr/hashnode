---
title: "Cannot redeclare block-scoped variable in TypeScript [Fixed]"
seoTitle: "Cannot redeclare block-scoped variable in TypeScript [Fixed]"
seoDescription: "In TypeScript, developers often run into the "Cannot redeclare block-scoped variable" error. This arises for two reasons: 1. Variable Redeclaration in Same"
datePublished: Sat Dec 02 2023 14:40:10 GMT+0000 (Coordinated Universal Time)
cuid: clpo5ufgs000109jo3pppeu16
slug: cannot-redeclare-block-scoped-variable-in-typescript-fixed
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701462077875/edc24eaf-2ef6-4ed3-b33f-ab15d254a02f.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701462488420/823f9de8-0c93-42fc-84bc-0de80795f4e7.webp
tags: error, programming-blogs, web-development, error-handling, typescript, frontend-development

---

In TypeScript, developers often run into the "Cannot redeclare block-scoped variable" error. This issue arises primarily from two reasons:

1. **Variable Redeclaration in the Same Block Scope:** When you attempt to declare a [variable](https://robiul.dev/javascript-variables-beginner-thinking) with the same name again within the same block scope.
    
2. **Conflict with TypeScript Global Typings:** When your chosen variable names clash with TypeScript's global typings.
    

This article will delve into both of these reasons, providing detailed explanations and offering solutions to address this common TypeScript issue.

## **Variable Redeclaration in the Same Block Scope**

When you have two variables with the same name within the same scope, it triggers the "Cannot redeclare block-scoped variable" error. This happens because, during declaration, a variable's value is stored in memory. If you try to declare another variable with the same name in the same scope, it attempts to save it in the same memory location, leading to an error.

Here's an illustrative example:

```typescript
let myVar = "Hello";  

let myVar = "World"; // Error: Cannot redeclare block-scoped variable 'myVar'.   
  
console.log(myVar);
```

In this example, the error occurs when attempting to redeclare `myVar` because `let` variables have [block-level scope](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/). The inner `myVar` is perceived as a redeclaration within the same block, leading to the error.

### Solution 1: Update the existing variable without re-declaring it

To avoid this error, a straightforward solution is to update the existing variable rather than declaring it anew.

If you're looking to assign a new value to the variable, the proper approach involves initially declaring it with [`let`](https://www.w3schools.com/js/js_let.asp) and subsequently changing its value without redeclaring.

```typescript
let myVar = "Hello";  

myVar = "World"; 

console.log(myVar); // 👉️ "World"
```

Unlike [`const`](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/) and `let`, variables declared with [`var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var) can be redeclared.

```typescript
var myVar = "Hello";  

var myVar = "World";

console.log(myVar); // 👉️ World
```

However, note that the `var` keyword behaves less intuitively and is generally advised against.

### Solution 2: Use Different Variable Names

Another effective strategy to circumvent this error is to employ unique names for different variables.

Consider the following TypeScript snippet as an example:

```typescript
let greeting = "Hello";

let newGreeting = "World"; // Introduce a distinct variable name.

console.log(greeting); // This is perfectly acceptable.
console.log(newGreeting); // This is perfectly acceptable.
```

By selecting different names for variables within the same block, you not only mitigate the error but also enhance the readability of your code. This practice aligns with best coding practices and facilitates collaboration among developers.

Remember, clear and unique variable names are not just about solving errors; they significantly contribute to the overall robustness and comprehensibility of your codebase.

### Solution 3: Change the variable's scope

If you prefer maintaining identical names for variables, an alternative is to modify the scope of one of the variables. By declaring a variable with the same name in a nested block, you establish a clear distinction between the variable in the outer scope and the one in the inner scope.

Let's illustrate this using TypeScript:

```typescript
let greeting = "Hello";
if (true) {
   let greeting = "World";    
    console.log(greeting); // World 
}  
console.log(greeting); // Hello
```

In this scenario, the two `greeting` variables coexist harmoniously due to their existence in different scopes. The initial `greeting` variable resides within the [module's scope,](https://web.dev/articles/global-and-local-scope#:~:text=Variables%20with%20module%20scope%20are,needs%20to%20access%20the%20variable.) while the subsequent one finds its scope within the block.

Crucially, this scope-adjusting approach isn't confined to [`if`](https://www.w3schools.com/js/js_if_else.asp) blocks; it can be applied to any nested block delineated by curly braces (`{` and `}`). The syntax involving curly braces allows for the creation of distinct blocks.

Here is the same example, without the `if` statement.

```typescript
let greeting = "Hello";
{
   let greeting = "World";    
    console.log(greeting); // World 
}  
console.log(greeting); // Hello
```

However, having variables with the same name in different scopes might confuse those reading your code. As a best practice, it's advisable to steer clear of such naming conflicts.

> Note: Using the `var` keyword for this approach would modify the value of the outer variable. This exemplifies one of the many reasons why the usage of `var` is discouraged.

## **Conflict with TypeScript Global Typings**

If you're encountering the "Cannot redeclare block-scoped variable" error, but you're certain there's no duplicate variable with the same name. likely, you've inadvertently attempted to modify the [global scope](https://www.w3schools.com/js/js_scope.asp).

Let's unravel this scenario through an illustration:

```typescript
const name = "Robiul";
// Cannot redeclare block-scoped variable 'name'.
```

Wait a minute! There's just one variable named `name` in our file. What's causing the hiccup?

When TypeScript encounters a file devoid of import or export declarations, it categorizes it as a script rather than a module. It makes its contents available in the global scope and to other modules.

Therefore, when an attempt is made to declare a variable with a name already in use, TypeScript raises an error.

Here's a practical example showcasing how this error manifests:

```typescript
// ⛔️ Error: Cannot redeclare block-scoped variable 'name'.ts(2451)
// lib.dom.d.ts(17330, 15): 'name' was also declared here.
const name = "Robiul Hasan";
```

In this instance, the `name` variable is declared somewhere in the typings for the DOM library, leading to a clash between the global type definition and the local variable declaration.

### Solution 1: Convert your file to an ES module

To fix the error, convert your file to an [ES module](https://www.knowledgehut.com/blog/web-development/commonjs-vs-es-modules), like this:

```typescript
let greeting = "Hello";

console.log(greeting); // Hello

export {};
```

By introducing this export statement, you've effectively signaled TypeScript to treat the file as a module, eliminating the error stemming from the clash between global scope and local variable declarations.

> Note: If you are working in a project where each file is treated as a module rather than a script, you can adjust your TypeScript configuration to force module detection in your `tsconfig.json`.
> 
> Enabling `moduleDetection` with the value `force` instructs TypeScript to treat every file as a module, irrespective of whether it contains imports or exports.
> 
> Here's an example configuration snippet for your `tsconfig.json`:
> 
> ```json
> {
>   "compilerOptions": {
>     "moduleDetection": "force"
>   }
> }
> ```

### Solution 2: Use an immediately invoked function expression(IIFE)

Another effective solution is employing an Immediately Invoked Function Expression ([IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)). This technique involves encapsulating the code segment containing the variable within a function that executes as soon as it's defined.

Here's a practical illustration:

```javascript
(function () {
  // ✅ works as expected
  let greeting = "Hello";
  console.log(greeting); // Hello //
})();
```

In this setup, the IIFE executes immediately upon script execution, ensuring the inner variable doesn't conflict with the global scope, providing a straightforward yet powerful resolution. This approach enhances code organization and maintains variable isolation.

## Resources

* [**Cannot redeclare block-scoped variable in TypeScript \[Fixed\]**](https://bobbyhadz.com/blog/typescript-cannot-redeclare-block-scoped-variable)
    
* [**Explained: Cannot redeclare block-scoped variable**](https://www.totaltypescript.com/cannot-redeclare-block-scoped-variable)
    
* [**How to Fix the "Cannot redeclare block-scoped variable" Error in TypeScript**](https://www.codingbeautydev.com/blog/typescript-cannot-redeclare-block-scoped-variable)