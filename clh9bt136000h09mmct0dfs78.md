---
title: "Javascript variables (Beginner thinking)"
seoTitle: "Javascript variables (Beginner thinking)"
seoDescription: "Javascript variables are named references to memory locations that can hold different types of data, such as numbers, strings, booleans, objects..."
datePublished: Thu May 04 2023 16:12:51 GMT+0000 (Coordinated Universal Time)
cuid: clh9bt136000h09mmct0dfs78
slug: javascript-variables-beginner-thinking
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684952007784/5b5d1011-1b5e-459a-9b62-845464699a98.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684952293845/11b9c8c6-9a3c-4004-8781-5a5c626a2919.jpeg
tags: variables, javascript, web-development, fundamentals, beginners

---

Programming is all about manipulating and displaying data, which can be any kind of information used in computer programs, such as social media usernames, age, and profile photos. To work with this data and create interesting things, programmers need a way to store and keep track of it. This is where the concept of variables more specifically **Javascript variables** comes in.

Variable is an essential concept in almost every programming language, and there is much to know and understand about it. It is important for us to have a clear and deep understanding of these concepts related to the Variable.

In this post, we will explore almost all of the concepts related to **Javascript variables** in programming, but from a beginner's perspective. We will keep things simple to understand, and use examples to explore everything.

Even if you are new to programming and don't have much knowledge about JavaScript, you will be able to understand all the concepts we cover.

So, let's get started!

## **Javascript variables**

In JavaScript, a variable is a named reference to a memory location that can hold different types of data, such as numbers, strings, booleans, objects, or functions. To access variable or modify the data stored in a variable, we use its name.

It's a little confusing, right?

let's have a look at the computer memory.

If you have a basic understanding of computer memory then you must know that Computer memory has millions of cells on it and every cell has its own address.

![javascript Variables Beginner Thinking (robiul.dev)](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952050726/05637dcb-66e9-4c08-a66a-eeef3ff5a894.jpeg align="center")

In our program, if we want to store value to access it later throughout the program, we have to keep it somewhere in the computer memory and we will need a way to call that value whenever we need.  
we could have done that using the memory address after storing the data in the memory.  
The problem is we can't use this address directly in our program. because you know the computer works in the binary system and in the binary system this memory address looks too weird and confusing. also, it's almost impossible to memorize.

Here variable comes in to solve this problem.

Variable gives us the simplest solution to handle it. We can simply create a variable and assign it to the value we want to store. now we don't need to memorize the weird and confusing memory address we can do the same using a simple and human-readable name.

When we are creating a variable and assigning a value to it. behind the since the Compilers and interpreters store the data inside the memory and replace the symbolic names of **variables** with the real data location/memory address.

![javascript Variables Beginner Thinking (robiul.dev).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952122668/b98658d6-7609-4b67-b215-dc350fdf01b9.jpeg align="center")

That means our data is stored in memory and the variable is pointing to this memory location.

> **Note:** In real scenarios, memory allocation is not as simple as I discussed here. also, Primitive type and Reference type values are treated differently when assigning them to **Javascript variables**. but for this post, I have avoided the advanced things and kept it simple so you can get an overall idea of how things work behind the scenes.

If you are still confused about **what are variables in javascript**, simply think of variables as named containers that hold information and can be referred to the data simply by naming the container.

That means,

* Creating a variable
    
* Giving a standard name to the variable
    
* Assigning a value to it.
    

Think of these steps as

* Taking a container
    
* Labeling it
    
* Putting something in this container.
    

![javascript Variables Beginner Thinking (robiul.dev).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952241518/883c0dc6-3453-4b62-bf5f-f5071bb66d59.jpeg align="center")

> **Note:** A Javascript variable is a container, not a value, this means that **variables** aren’t themselves values; they are a named container for values.

## Variable Declaration

Before you use a variable in a JavaScript program, you must create or define variable, we call this declaring a variable.

we can Declare a JavaScript Variable using `var` or \`let\` :

```javascript
var name; 
let age;
```

Here we are creating two variables, one using var and one using let.

var and let are the keywords that tell JavaScript you’re declaring a variable.

name and age are the names of those variables.

In Javascript, Semicolons(;) are totally optional (unless you want to have multiple statements in a single line, of course). (similar to a full stop(.) in the English language.)

> Note: Though Semicolons(;) are optional in javascript, there are many languages where Semicolon(;) is a big factor. In those languages you must end the line using a semicolon otherwise will occur an error to your program.

In **javascript multiple variable declaration** can be done with the same `var` or \`let\` keyword:

```javascript
var name, age;
let birthYear, address;
```

> There is another keyword to declare **Javascript variables** which is const. This is used to declare the constant variables in javascript.
> 
> ```javascript
> const  Pi = 3.1416
> ```
> 
> we will talk about this in any other blog.

## Naming Variables

Not only in JavaScript but also, in all other languages variables must be identified with unique names following some rules and regulations which is called **naming variables**. These unique names are called identifiers. These Identifiers or names can be short (like \`a\`, \`b\`, and \`c\`) or more descriptive (\`age\`, \`name\`, \`userName\`).

### Javascript variable name rules

There are some general rules to follow when we are **naming variables** (unique identifiers) for the variable.

Here are the rules below:

* Names can contain letters, Number digits(0-9), underscores \`\_\`, and dollar signs \`$\` but Spaces and special symbols/punctuation characters (like @, !, #, etc.) are not allowed to be used in the variable's name.
    

> Note: In Javascript '\_' and '$' are just like letters. They don't have any special meaning.

* Variable names must be started with either a letter, an underscore \`\_\`, or the dollar sign `$` in javascript. It is not allowed to start variable names using numbers (0-9).
    
* JavaScript Names/identifiers are case sensitive (Variables named \`apple\` and \`APPLE\` are two different variables.).
    
* There are some reserved words, which cannot be used as variable names in your program because they are used by the language itself.
    

`For example: let, var, for, and function are reserved.`

The code below gives an Uncaught SyntaxError:

```javascript
let var = 5;   //  Uncaught SyntaxError: Unexpected token 'var'
let function = 5; // Uncaught SyntaxError: Unexpected token 'function'
```

* In JavaScript, When the variable name contains multiple words, it is generally written in camelCase.
    

That is: words go one after another, every word except the first one starting with a capital letter.

`For example, firstName, lastName, birthYear, etc.`

* It is possible to use almost any language in a variable name, but not recommended. We should use English in variable names even if we’re writing a small script. so that if people from other countries need to read it they can read it. Because we will write code for global developers not only for our region.
    

Here are some valid and invalid variable names below:

```javascript

// Example of valid variables names
let camelCased         //  first word is lowercase any additional word starts with an uppercase letter
let here2num                  // number in the middle, but not starting with numbers
let JAVASCRIPT_IN_UPPERCASE       // uppercase letters with underscores
let _Javascript_              //start and end with an underscore, with letters in the middle
let $_$                       // dollar signs and underscores
let $_foo3                // mix the dollar sign, underscores, letters and numbers
let _12foo           //start with underscores and contain numbers and letters
let _                 //   contains only underscore
let $             // contain only a dollar sign


// Example of invalid variables names

let random%         //  Don't use the percentage symbol
let 11years           //  Don't start with number(s)
let some-let      //  Don't use dashes
let one variable   //  Don't use spaces
let function           //  Don't use reserved keywords
```

### Naming variable Good practices

Giving a good name to the variable is one of the most important and complex skills in programming. Proper descriptive variable names can create a good impression for a programmer in the viewer's eyes.

In a real project, most of the time a programmer spends modifying and extending an existing code base rather than writing something completely new. When we return to the code after doing something else for a while or maybe for a long period of time, it’s much easier to get back into a flow for those codes that is well-labeled. Or, in other words, when the variables have been declared with good names.

So, Please spend time thinking about the right name when you are declaring a variable. Doing so will make you benefited in the future.

* Though variable names can be created in any way you want, it's a good practice to use human-readable, obvious meanings and maximally descriptive (the value the variable is referencing). If we name a variable as “user” then we should name related variables as currentUser or newUser.
    
* Stay away from short names like a, b, and c. These kinds of short names are easy to type. But these are only useful in small programs. When you will work on a big project, will forget the context of these kinds of names.
    

> Note: Though There is no limit to the length of the variable name and it can be almost unlimited in length, You should avoid creating extremely long variable names. Shorter variable names help the JavaScript engine to execute the program faster.

* Since JavaScript is case-sensitive, apple and Apple are two different identifiers. But we should not use both of them in our program. Because this will occur confusion in the long term.
    
* The best way to create a variable is to use multiple words in camelCase. (e.g., \`myVarName\`).
    

## Undefined value of a variable

When we declare a variable without assigning a value to it will have the value `undefined`.

It's the default behavior of javascript. Though this container should be empty, it is not. It still contains a value that is \`undefined\`.

> Note: `undefined` is one type of data in javascript. we will see about `undefined` and other data types in any other blog in detail.

If you want to see their value, you can do that by simply doing \`console.log()\` in your web browser's console the output will be \`undefined\`.

```javascript
let name, age, birthYear;
console.log(name);          // undefined
console.log(age);           // undefined
console.log(birthYear);     // undefined
```

## Undeclared variable

Suppose you want to use a variable in a statement, but you haven't declared this variable yet. In this case, your code will throw a \`ReferenceError\` showing that the variable is not defined. In short, if we want to access an Unassigned or **undeclared variable**, the code will throw a runtime error.

Example:

```javascript
console.log(xyz);  // ReferenceError: xyz is not defined
```

Try running the above line in the browser console.

In the real program, You should never try accessing a variable without declaring it.

> Note: Don't get confused with the undefined and Unassigned/**Undeclared variable** — they are very different things. An undefined variable is a variable that has been declared in the program but has not been initialized with a value. In contrast, an undeclared variable is a variable that has not been declared yet.

## Variable Assignment

After the declaration has been completed, we can use the equal(\`=\`) sign for **Variable Assignment**:

Example:

```javascript
let age;
age = 22;
```

where the `age` is the name of the variable and it is assigned a value of `22`.

> Note: In JavaScript, the equal sign (\`=\`) is an "assignment" operator, not an "equal to" operator like in algebra. Though the following does not make sense in algebra:
> 
> ```javascript
> x = x + 10;
> ```

But In JavaScript, it makes perfect sense:

First It calculates the value of `x + 10` and assigns the result to variable \`x\`. In simple words, The value of `x` is incremented by `10`.

> Note: in JavaScript, the "equal to" operator is written like `==`.

Also, the **variable declaration** and initialization can be combined. that means variable initialization can be done in the declaration:

```javascript
var greetings = "Hello";
let name = "Robiul"

// or,
var greetings = "Hello", name = "Robiul";

//The same declaration can even span across multiple lines using comma(,):

var greetings = "Hello", 
      name = "Robiul";
```

> Note: we can do **Variable Assignment** from user input
> 
> ```javascript
> // Gets user input
> var name = prompt("What is your name?");
> var age = prompt("What is your favorite age? ");
> console.log(name)  
> console.log(age)
> ```

## Changing Variable

The meaning of the word ‘variable’ is anything that can vary. That means once the initialization is finished we can change or update the value of the variable later on in the program if required.

It is similar to re-initializing the variable. We can do Updating or Re-assigning or **Changing Variable** by just typing the name of the variable followed by an equals sign(\`=\`) and then followed by the new value we want it to store.

```javascript
var greetings = "Hello";
let myHobby = "Drawing";
console.log(greetings);   // Hello
console.log(myHobby);   // Drawing

// changing the value 
greetings = "Hi";
myHobby = "Programming"
console.log(greetings);   // Hi
console.log(myHobby);   // Programming

//   also, we can change the value as many times as we want:

let message;
message = "Hello";
console.log(message);  // Hello
message = "World"; 
console.log(message);  // World
```

`javascript variable doesn't contain the history of the variable, which means when we change the value of a variable it removes the old data and stores the new one.`

> Note: There are a few functional programming languages, like Scala or Erlang that don't allow changing variable values.  
> In such languages, once the value is assigned in a variable, it’s there forever. If we want to reassign the variable or want to change the value of the variable, the language forces us to create a new variable (declare a new variable). We can’t reuse the old one.

## Accessing JavaScript variables

As a beginner, you might be thinking about what is the procedure to access/use the value that is stored in a specific variable. It's simpler than declaring and assigning the variable. You just need to write the name of the variable that contains the value you want to access and you are done. This things also called “referencing a variable”.

```javascript
// Declare and initialize the variable
var myNumVariable = 85
let myTextVariable = 'This is text.'

// Access the values in myNumVariable and myTextVariable
myNumVariable
// 85
myTextVariable
//  'This is text.'


// Re-assign myNumVariable and myTextVariable
myNumVariable = 50
myTextVariable = 'This is a updated Text'


// Access the values in myNumVariable and myTextVariable again
myNumVariable
// 50
myTextVariable
// 'This is a updated Text'
```

## Basic usage of variables

* Once you declare a variable and initialize it, you can reference this variable by name anywhere elsewhere in your code.
    

```javascript
var x = 10;
x + 2;
console.log(x)   // 12
```

* You can use an already declared variable when declaring a new variable.
    

```javascript
var x = 100;
var y = x + 102;
console.log(y)  // 202
```

* you can do all kinds of arithmetic operations with **JavaScript variables**, using operators like \`=\`, \`+\`, \`\*\`, and more. :
    

```javascript
let x = 5 + 2 + 3;
console.log(x)  // 10
```

* You can also add a string to another string, but strings will be concatenated:
    

```javascript
let x = "John" + " " + "Doe";
console.log(x)   // John Doe
```

> Note: During arithmetic operations If you put a number in quotes, the rest of the numbers will be treated as strings, and all of them will be concatenated. Now try this:
> 
> ```javascript
> let y = "5" + 2 + 3;
> console.log(y)   // 523
> ```
> 
> This is called coercion in javascript

## Why should we use variable

So far we have discussed what is variable, how to create it, and how it works in our program. But haven't discussed why this is so important and why should we use the variable.

Let's have a look at this too. we will discuss some point on how variable helps programmers to write optimized and efficient code :

To Understand these points let's see a program of a pretty simple and state-forward game called guess my number. This game logic is very simple, we will use a number in our code and the user will have to guess the number if the user guesses the correct number our program will show a successful message and if the user is wrong the program will show a failed message.

```javascript
if(userInput==20){
  console.log("Hurrah, You guess the correct number.");
}else if(userInput<20){
  console.log("Sorry, Your guessed number is small. Please try a bigger one.")
}else if(useInput>20){
  console.log("Sorry, Your guessed number is Big. Please try a bigger one.")
}
```

Here in this program, we have used the number `20` to make our program logic. This program will perform fine but this program is not well coded.

let's see what's wrong with this program and why this is not well coded and how variable makes our life easy and help us to make our code more efficient and optimized:

* The first problem with this program is we have to memorize the number `20` or have to check the number again and again whenever we will use it in our program. Maybe it doesn't seem a big problem for a small program and simple value like this but imagines a program that has a thousand lines of code and maybe hundreds of value like this number or maybe some huge numbers like `204025021`, `12242250221` and we can't memorize all of them.
    
    Here variable helps us by giving a simple solution to deal with this kind of problem. we can simply store the value on a variable and just use a simple and descriptive name rather than using scary and ugly numbers every time when we need. so, Now we don't have to remember the number or any kind of value we can just remember the name we have given to the variable and use it anywhere in our program.
    

```javascript
let myNum = 20;
if(userInput==myNum){
  console.log("Hurrah, You guess the correct number.");
}else if(userInput<myNum){
  console.log("Sorry, Your guessed number is small. Please try a bigger one.")
}else if(useInput>myNum){
  console.log("Sorry, Your guessed number is Big. Please try a bigger one.")
}
```

* Now here comes the second problem with this code. that is when we will try to change the number we have to change the number from every place where we have used the number. and imagine when we will work on a big project we have to use a variable in several places. if we would need to change the value from all the places how painful and time-consuming it would be.
    
    Here variable gives us an opportunity to change the variable in all places by changing it in one place. we can store our value in a variable and use it anywhere in our program. whenever we need to change it we can just simply change it from one place and it will change everywhere.
    

```javascript
let myNum = 20;
console.log(myNumber) // 20
if(userInput==myNum){
console.log(myNumber) // 20
  console.log("Hurrah, You guess the correct number.");
}else if(userInput<myNum){
  console.log(myNumber) // 20
  console.log("Sorry, Your guessed number is small. Please try a bigger one.")
}else if(useInput>myNum){
  console.log(myNumber) // 20
  console.log("Sorry, Your guessed number is Big. Please try a bigger one.")
}
// change the value
myNum = 30;
console.log(myNumber) // 30
if(userInput==myNum){
  console.log(myNumber) // 30
  console.log("Hurrah, You guess the correct number.");
}else if(userInput<myNum){
  console.log(myNumber) // 30
  console.log("Sorry, Your guessed number is small. Please try a bigger one.")
}else if(useInput>myNum){
  console.log(myNumber) // 30
  console.log("Sorry, Your guessed number is Big. Please try a bigger one.")
}
```

how simple it is! right?

* Another program with this program is we are using the number in a statical way. That means our program is not dynamic now. If we need any changed value we have to edit the source code which is very bad. To write a modern program we should have a feature to change the value dynamically.
    
    Here Variable gives us the best and simplest way to do that. we can simply create a variable and assign the value of the variable from a user input rather than assigning it statically.
    

```javascript
  let myNum =  prompt("enter a number?");
if(userInput==myNum){
  console.log("Hurrah, You guess the correct number.");
}else if(userInput<myNum){
  console.log("Sorry, Your guessed number is small. Please try a bigger one.")
}else if(useInput>myNum){
  console.log("Sorry, Your guessed number is Big. Please try a bigger one.")
}
```

Now our code is dynamic we can change the value whenever we want without changing or editing the source code.

Thus, variable helps us to write optimized, developer-friendly, and easy-to-understand code.

> Note: Though variable helps us in many ways. but too many variables can harm the code performance very badly and it's can increase the server cost. so, we should be careful when we are declaring a variable.

## Recap

* A variable is a computer memory location paired with an associated symbolic name, which contains some information or data referred to as a value.
    
* We can simply think of **Javascript variables** as named containers that hold information and can be referred to the data simply by naming the container.
    
* We can Declare a JavaScript Variable using `var` or `let`.
    
* All **JavaScript variables** must be identified with unique names. These unique names are called identifiers.
    
* There are some general rules to follow when we are constructing a name (unique identifiers) for the variable.
    
* A variable declared without a value will have the value undefined.
    
* A variable that has not been declared yet is called an undeclared.
    
* After the declaration, we can use the equal(\`=\`) sign to assign value to the variable
    
* You can combine **variable declaration** with variable initialization. that means initialization can be done in the declaration.
    
* Once a variable has been initialized with a value, you can change (or update) that value anytime and anywhere within its scope by giving it a different value.
    
* We can access a value of a variable simply by using the name of the variable. This is also called “referencing a variable”.
    
* You can reference a variable by name elsewhere in your code.
    
* You can use a variable when declaring other variables.
    
* You can do arithmetic with **JavaScript variables**, using operators like \`=\` and \`+\`.
    
* You can also add strings, but strings will be concatenated.
    
* variable helps us to write optimized and efficient code. Though it is helpful in many ways, too many variables can be harmful. so, we should be careful of it.
    

## Resources

* https://www.w3schools.com/js/js\_variables.asp
    
* https://javascript.info/variables
    
* https://www.javascripttutorial.net/javascript-variables
    
* https://www.freecodecamp.org/news/javascript-variables-beginners-guide
    
* https://www.scaler.com/topics/javascript/javascript-variables/
    
* https://blog.alexdevero.com/javascript-variables-introduction/
    
* https://www.freecodecamp.org/news/understanding-let-const-and-var-keywords
    
* https://medium.com/@avishaa27/what-are-variables-in-javascript-3aa9a3324a1e
    
* https://www.javascript.com/learn/variables
    
* https://www.toolsqa.com/javascript/javascript-variables
    
* https://data-flair.training/blogs/javascript-variable-tutorial/
    
* https://medium.com/@shreyanshshah242/variables-in-javascript-13099376b279