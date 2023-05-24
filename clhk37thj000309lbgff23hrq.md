---
title: "Is javascript compiled or interpreted language?"
seoTitle: "Is javascript compiled or interpreted language?"
seoDescription: "while JavaScript is commonly thought of as an interpreted language, it is actually a JIT compiled language. Modern JavaScript engines use a JIT compiler..."
datePublished: Fri May 12 2023 04:57:52 GMT+0000 (Coordinated Universal Time)
cuid: clhk37thj000309lbgff23hrq
slug: is-javascript-compiled-or-interpreted-language
canonical: https://dev.to/robiulhr/is-javascript-compiled-or-interpreted-language-l20
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684952659445/61ccf7f5-6385-487d-8744-342f1e89f7b4.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684953245281/6eff7767-c712-4743-a0f7-80355fcc182a.jpeg
tags: tutorial, programming-blogs, javascript, web-development, programming-languages

---

## Introduction

You have probably read that JavaScript is an interpreted language, while others argue that it's not an interpreted language and that it's actually a compiled language. **Is javascript compiled or interpreted**?

This can be confusing,

I was often confused because I received conflicting answers whenever I read books or articles about JavaScript being an interpreted or compiled language. But the truth is that it depends on how the language is implemented.

Let me explain.

To clarify this point, let's first examine what are compiler and interpreter also the difference between them

## Compiler

A compiler is a software tool that translates human-readable source code into machine-executable code. The process of compilation involves several stages, including

* lexical analysis
    
* syntax analysis (parsing)
    
* semantic analysis
    
* code generation
    
* optimization
    

During lexical analysis, the compiler breaks down the source code into a series of tokens, which are individual units of meaning. For example, in the statement `"x = 5 + 3;"`, the tokens would be `"x"`, `"="`, `"5"`, `"+"`, and `"3"`. The lexer also assigns a type to each token, such as "identifier", "operator", or "literal".

Then, during syntax analysis (parsing), the compiler checks the order and structure of the tokens to ensure that they form a valid program. This involves analyzing the grammar of the programming language and constructing a syntax tree that represents the structure of the program.

After the syntax analysis is complete, the compiler performs semantic analysis to check for logical errors in the code. This involves verifying that the program follows the rules of the language, such as type checking, scoping rules, and function calls.

Once the compiler has verified the correctness of the program, it generates machine code or bytecode that can be executed by the computer. This involves translating the syntax tree and semantic information into low-level instructions that can be executed by the computer's hardware.

Finally, the compiler performs optimization to improve the efficiency of the generated code. This process involves analyzing the code and making changes to improve the memory usage.

Overall, the compiler is an essential tool for translating human-readable source code into machine-executable code. The compilation process involves several stages, each of which is critical for producing correct and efficient code.

## Interpreter

An interpreter is a program that reads and executes code written in a high-level programming language directly, without requiring an intermediate compilation step. Unlike a compiler, which translates the entire source code into machine code before execution, an interpreter reads and executes the source code line by line, translating and executing each statement as it is encountered.

When an interpreter runs a program,

* it first performs lexical analysis and parsing of the source code to generate an abstract syntax tree (AST) representing the program's structure.
    
* The interpreter then walks through the AST, executing each node in turn. During execution, the interpreter may generate and manipulate additional data structures to represent the state of the program, such as a symbol table for tracking variable values.
    

One advantage of using an interpreter is that it allows for more dynamic and interactive development, as programmers can test and modify their code on the fly without having to recompile the entire program. However, interpreting code can be slower than executing compiled code, since the interpreter has to perform additional work to translate and execute each statement.

Overall, an interpreter provides a convenient way to execute code in a high-level language, but may not be as performant as compiled code in certain situations.

## Compiler vs. Interpreter in a simple way

![Is javascript compiled or interpreted language? (robiul.dev)](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952710909/910e240e-0162-421f-8e63-11e4707b2947.jpeg align="center")

There is a lot of technical information about compilers and interpreters, so let's make it simple:

And like everything else in life, let's try to understand it with a cup of tea.

Let's say you want to make a cup of black tea, you go to Google and search for the ingredients list, this is what you came up with:

* Black tea leaves
    
* Water
    
* Sugar (optional)
    
* Milk (optional)
    

There are 2 ways to make the tea, the Compiler or the Interpreter way.

The compiler will first, before doing any steeping, organize all the ingredients in front of him, the specific amounts of every single ingredient, only then, will he steep all the ready components of the tea.

The interpreter will take his cup and will start by reading the ingredients, line by line. he will boil the water, add the tea leaves, steep them for a few minutes, add sugar or milk if desired, and then strain the tea into the cup.

The build (preparation) time of the compiler will be longer than the interpreter's. However, the run (steeping) time will be much shorter.

Now that you know the difference let’s talk about JavaScript.

## Is javascript compiled or interpreted Language?

When I first started learning JavaScript, I, like many others, was taught that it was an interpreted language, and I believed it for a long time. However, after conducting further research, I have come to realize that this is not entirely accurate.

While many people still consider JavaScript to be an interpreted language, there is evidence to suggest that it is actually a compiled language. One example of this can be seen in the way that the JavaScript engine handles bugs.

When you encounter a syntax error in your JavaScript code, the engine will typically alert you to the problem before it even begins executing the code. This suggests that the code is compiled and validated before it is executed, which is a characteristic of compiled languages.

You can try this for yourself by opening the following HTML code in your browser and checking the console:

```js
console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World!);
```

The last line of code is missing a closing quotation mark, which should trigger a syntax error. However, if JavaScript were truly an interpreted language, the console would have already printed the first nine lines before throwing an error.

Instead, the program crashes immediately,

```js
Uncaught SyntaxError: Invalid or unexpected token
```

That indicates that it was compiled and validated before execution.

While there is still debate over whether **Is javascript compiled or interpreted**? it's clear that it's not entirely accurate to call it an interpreted language.

Another way to prove that JavaScript is not an entirely interpreted language is through the concept of `hoisting`. For example, consider the following code:

```javascript
max(1, 2);
// 2
function max(num1, num2){
  return num1 > num2 ? num1 : num2;
}
```

In traditional programming languages, a function must be defined before it can be called. However, in JavaScript, the function can be called before it is defined. This behavior is known as `hoisting`, and it's a fundamental aspect of how JavaScript works.

```md
Note: We will explore more about `hoisting` in other blog for now this explanation is enough.
```

How does the JavaScript engine know about the `max` function before it reaches the declaration? The only reasonable answer to this question is that the code must first be compiled before execution.

So, **Is javascript compiled**?

![Is javascript compiled or interpreted language? (robiul.dev)](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952769795/48a35db3-67a8-4d3d-b278-f48ce9f7d2cc.jpeg align="center")

Well, it's complicated. In the past, every programming language was fairly easy to categorize as either compiled or interpreted. However, with the modern approach of running source code, a sort of "in-between" area has been created.

## How does JavaScript actually get translated?

JavaScript has come a long way since its inception as a simple scripting language. In the early days, JavaScript engines were only interpreters, which executed code line by line. However, as JavaScript became more popular and its use cases expanded, performance issues emerged. Interpreting code on-the-fly resulted in a loss of performance, especially for complex applications. This led to the development of new engines that use a just-in-time (JIT) compiler.

A **JIT compiler** is different from traditional compilers, such as those used for C++. Traditional compilers have plenty of time to optimize the code during compilation, but the **JIT compiler** must compile code just before it's executed. As soon as the JavaScript code is about to run, it gets compiled into executable bytecode.

Despite the differences in how JavaScript is compiled compared to other compiled languages, the process still follows some of the same rules as traditional compilers. The JavaScript code is parsed before execution, which makes it look like a parsed language. However, the code is converted to binary form before execution.

To better understand this process, let's take a closer look at how code execution works behind the scenes:

* First, the code is transpiled using tools like Babel or Webpack.
    
* The transpiled code is given to the engine, which parses it to an Abstract Syntax Tree (AST).
    
* The AST is then converted to bytecode that is understood by the machine. This is an Intermediate Representation (IR), which is further optimized by the **JIT compiler**.
    
* After optimization, the JS Virtual Machine (VM) executes the code.
    

```javascript
Some people argue that the JS VM is "interpreting" the bytecode, but this is not entirely accurate. If we were to use that definition, we would also have to say that Java, which is another JVM-driven language, is also interpreted.
```

Thus, we can conclude that JavaScript is executed in three phases:

* Parsing
    
* Compiling
    
* Executing
    

JavaScript code is initially interpreted before any execution begins. For example, consider the following code:

```javascript
console.log("Hello");
for(var i = 0;i<4;i++) {
    console.log(Hello);
}
```

The output shows the interpreter behavior in the above code example, where first `Hello` is printed to the console, and then an error is reported. This output strongly supports the fact that JavaScript is an interpreted language.

While it may seem like JavaScript code is being executed line by line, this is only true during the parsing phase. In reality, the entire code is compiled at once to convert it into machine-readable code before execution. Therefore, JavaScript is a just-in-time compiled language that uses an interpreter in its first phase.

```md
Note: JavaScript can operate in an interpreted manner in older browsers. However, every modern browser currently supports "JIT", so JavaScript code is always compiled. Whether JavaScript is compiled or interpreted depends on the environment in which it is run. If it runs in older browsers, it's interpreted. If it runs in modern browsers, it's compiled.
```

## Explaining JIT in JavaScript

Now that we have a basic understanding of how JavaScript works and what a **JIT compiler** is, let's delve deeper into how JIT compiler work and why they're important.

But don't worry, we won't get too technical with jargon. Instead, we'll explore JIT compiler in simple terms to understand how they work, why they're important, and the reason they were introduced in the first place.

JIT (just-in-time) compilation is a technique used by modern JavaScript engines to improve the performance of JavaScript code. Unlike traditional compilers that optimize code during compilation, JIT compiler take a middle-ground approach. They initially interpret the code and then selectively compile parts of it that are used repeatedly. This approach balances fast start-up time with improved performance.

When a JavaScript engine encounters a function, it can either interpret the code on-the-fly or compile the code before execution. Interpreting the code can be faster to start execution but slower in terms of overall performance, as the code is translated line-by-line each time the function is executed. Compiling the code before execution can be slower to start, but it can result in faster execution due to machine code optimizations.

In this approach, the code is compiled into machine code, which is then executed by the processor.

**JIT compiler** take a middle-ground approach, where they initially interpret the code and then selectively compile parts of it that are used repeatedly. As a result, the JIT compiler offers a balance of fast start-up time and improved performance.

![Is javascript compiled or interpreted language? (robiul.dev)](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952812308/70ce41af-7fea-4210-a81b-e5e789272d14.jpeg align="center")

To understand how JIT compilers work, let's consider an example:

```js
function add(a, b) {
  return a + b;
}

for (let i = 0; i < 100000000; i++) {
  add(i, i + 1);
}
```

In this code, we have a simple `add` function that adds two numbers and a loop that calls this function `100` million times with different inputs.

When the JavaScript engine first encounters this code, it will interpret it on-the-fly and execute it. However, as the loop runs repeatedly, the engine detects that the `add` function is being called repeatedly and decides to compile it to machine code to improve performance.

The **JIT compiler** analyzes the code and optimizes it for the specific inputs being used in the loop.

For example, it may decide to inline the `add` function, which means replacing the function call with the actual addition code, eliminating the overhead of calling a function. Additionally, it may also perform other optimizations such as constant folding or dead-code elimination, which remove unnecessary computations.

Overall, the **JIT compiler** help improve the performance of JavaScript code by selectively compiling parts of it that are used repeatedly, while still allowing for fast start-up times.

Now that we have a better understanding of how the **JIT compiler** works, let's delve into the issues we previously discussed and their underlying causes.

## Why the Pre-execution syntax error alerts

Let's explore the reason behind syntax error alerts in JavaScript using the same example we discussed earlier.

```js
console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World from javascript!");
 console.log("Hello World!);
```

In the case of the code example provided, the JavaScript engine compiles the code before execution, and the syntax error is detected during the compilation phase. This is because the engine uses the `JIT` compiler that optimizes code on the fly as it's executed. When the engine encounters an error during the compilation phase, it immediately throws an error without executing any code.

Therefore, the fact that JavaScript detects syntax errors during the compilation phase suggests that it's more like a compiled language than an interpreted one.

## What is the story of hoisting?

Let's now understand the hoisting in the context of `JIT` engine using the code we used before:

```javascript
max(1, 2);
// 2
function max(num1, num2){
  return num1 > num2 ? num1 : num2;
}
```

So, how does the JavaScript engine know about the `max` function before it reaches the declaration?

![Is javascript compiled or interpreted language? (robiul.dev)](https://cdn.hashnode.com/res/hashnode/image/upload/v1684953203202/c5ad1241-6c18-490e-aa33-5aab132feee1.webp align="center")

The answer lies in the Just-In-Time (`JIT`) compilation process that occurs behind the scenes when JavaScript code is executed in modern browsers.

During the optimization step, the **JIT compiler** can analyze the code to determine which functions are likely to be called frequently and which variables are likely to be accessed repeatedly. By identifying these patterns, the compiler can optimize the code for faster execution, which can result in significant performance gains.

In the case of hoisting, the compiler can recognize the pattern of a function being declared at the top of its scope and optimize the code accordingly.

## Conclusion

In summary, while JavaScript is commonly thought of as an interpreted language, it is actually a Just-In-Time compiled language. Modern JavaScript engines use a **JIT compiler** to optimize the code for execution. This compiler allows JavaScript to be executed much faster and in an efficient way than traditional interpreted languages. While the compiling of Javascript works in a different way, if compared to other compiled languages, it still follows some rules that reflect the process of compiling.

JavaScript code is parsed before execution, which makes it look like a parsed language, but the code is actually converted to binary(machine code that is directly executed by the computer's hardware) form before execution. This conversion process involves several steps, including transpiling the code, parsing it to an Abstract Syntax Tree (`AST`), converting it to bytecode, and optimizing it with a `JIT` compiler.

So, to answer the question "**Is javascript compiled or interpreted** language?" the answer is that it is a bit of both. It is interpreted in older browsers, but in modern browsers, it is compiled with the help of a **JIT compiler**.

## Resource:

* https://www.linkedin.com/pulse/javascript-compiled-language-st%C3%A9phane-moreau/
    
* https://stackdiary.com/tutorials/is-javascript-a-compiled-or-interpreted-language/
    
* https://almogad.medium.com/javascript-is-it-compiled-or-interpreted-9779278468fc
    
* https://www.geeksforgeeks.org/is-javascript-interpreted-or-compiled/