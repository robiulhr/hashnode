---
title: "I Made a Custom Version of Express.js Framework: Cute Express"
seoTitle: "I Made a Custom Version of Express.js Framework: Cute Express"
seoDescription: "Cute Express is a lightweight and feature-rich web framework that covers almost all basic and a few advanced features of Express.js. It's like having a s..."
datePublished: Wed Aug 09 2023 01:30:09 GMT+0000 (Coordinated Universal Time)
cuid: cll31zhmq00030ajzf84f7qdi
slug: i-made-a-custom-version-of-expressjs-framework-cute-express
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691477948422/4ea39d46-66b3-4666-b25e-e0ad6a0da00f.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691478125585/cf74158e-40a9-4c87-9903-5a2bb4d57684.webp
tags: express, javascript, web-development, nodejs, backend

---

## Introduction

Hello there, fellow JavaScript and node js learner! We all know that practice makes perfect, and what's better than a challenge to level up our skills? I found myself on a mission to discover a project that could take my JavaScript and node js knowledge to the next level. Something interesting, effective, and practical, where I could put all my learning into action.

And guess what? I found it - Cute Express!

It's my very own version of the famous Express.js framework. I built it from the heart, driven by my passion for coding and inspired by the elegance of Express js.

In this article, I'm thrilled to show you the cool things I've created and that is Cute Express.

Let's dive in and explore its features and functionalities together!

## What is Cute Express?

Cute Express is a lightweight and feature-rich web framework that covers almost all basic and a few advanced features of [Express.js](https://expressjs.com/). It's like having a smaller and cuter clone, or you could even consider it a pocket-sized version of Express.js.

However, let's be clear – Cute Express isn't trying to conquer the web development world and It's not intended for industry use or to replace anything. It's a fun project I crafted purely for practicing my JavaScript and [Node.js](https://nodejs.org/en) skills.

Unlike serious industry tools, Cute Express is your coding companion for creative experimentation. It's my way of exploring the world of web frameworks while having a blast.

So, join me as we unravel the adorable charm and practicality of Cute Express  
together!

## Features of Cute Express

Now, let's talk about the real deal – the features of Cute Express that I've crafted with my own hands tailored to my coding style and preferences.

Cute Express is all about embracing the tried-and-true features of Express.js – no frills, no extra fuss.

From routing to handling different [HTTP methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods), Cute Express is packed with functionalities that mirror those of actual express js. I wanted to challenge myself and see if I could recreate the Express.js magic in my unique way, sticking to its core functionalities.

Just like Express.js, Cute Express lets you define routes, handle middleware, and respond to various [HTTP requests](https://www.geeksforgeeks.org/different-kinds-of-http-requests/). It's all about creating a smooth and intuitive experience for developers, just on a smaller scale.

## Setting Up a Basic Server with Cute Express

let's start our journey by setting up a basic server.

To begin, let's install Cute Express as a dependency:

```bash
npm install cute-express
```

Learn more about the installation process from [Installing Cute Express](https://robiulhr.github.io/cute-express/getting_started/hello_world.html).

Now, let's create a simple server using Cute Express:

```javascript
const cuteExpress = require('cute-express') 
const app = cuteExpress() 
const port = 3000  

app.get('/', (req, res) => {
   res.send('Welcome to Cute Express!');
})  

app.listen(port, () => {
   console.log(`Example app listening on port ${port}`)
})
```

Do you notice the resemblance? The process mirrors the simplicity of creating a server in Express.js. With just a few lines of code, we have a basic server that listens on port `3000`. As you visit `http://localhost:3000` in your browser, you'll be greeted with the message `Welcome to Cute Express!`

## Routing with Cute Express

Ah, [routing](https://robiulhr.github.io/cute-express/guide/routing.html) – the heart and soul of any web framework. Let's dive into the world of routing in Cute Express, where we'll navigate through URLs and create delightful paths for our users to follow.

In Cute Express, routing is a breeze, and it'll feel just like home if you've ever worked with Express.js. Defining routes is straightforward:

```javascript
const cuteExpress = require('cute-express'); 
const app = cuteExpress();  

// Define routes 
app.get('/', (req, res) => {
   res.send('Welcome to Cute Express!'); 
});  

app.get('/about', (req, res) => {
   res.send('Learn more about Cute Express.'); 
});  

app.post('/contact', (req, res) => {
   // Handle contact form submission 
});  

// Start the server 
app.listen(3000, () => {
   console.log('Server is running on port 3000'); 
});
```

Notice the familiarity? We're defining routes using [`app.get()`](https://robiulhr.github.io/cute-express/api_reference/api_reference_1.x.html#app-get-path-callback-callback) and [`app.post()`](https://robiulhr.github.io/cute-express/api_reference/api_reference_1.x.html#app-post-path-callback-callback) – just like you would in Express.js. When a user visits `/about`, Cute Express will greet them with `Learn more about Cute Express.`

But wait, there's more! Cute Express also supports dynamic routing with parameters:

```javascript
app.get('/user/:id', (req, res) => {
   const userId = req.params.id;
   res.send(`Hello, User ${userId}!`); 
});
```

When a user visits `/user/42`, Cute Express will warmly say, `Hello, User 42!` This flexible routing lets you create personalized experiences for your users.

And guess what? You can even use regular expressions as paths, giving you the flexibility to match complex patterns and create advanced routing logic.

```javascript
// Using regular expressions as paths 
app.get(/\/product\/(\d+)/, (req, res) => {
  const productUrl = req.url;
  res.send(`Product ID: ${productUrl.split("/")[2]}`);  
});
```

## Middleware in Cute Express

[Middleware](https://robiulhr.github.io/cute-express/guide/writing_middleware.html) – the mystical bridge between requests and responses. Just like Express.js, Cute Express supports middleware functions that can handle a wide range of tasks, from logging to authentication.

Declaring middleware in Cute Express is a breeze. Simply use [`app.use()`](https://robiulhr.github.io/cute-express/api_reference/api_reference_1.x.html#app-use-path-callback-callback) and unleash the power:

```javascript
const cuteExpress = require('cute-express');
const app = cuteExpress();

// A simple middleware
app.use((req, res, next) => {
  console.log('A request is coming in...');
  next(); // Don't forget to call next to continue the flow
});

// More middleware functions...
```

See? You can log messages, check authentication, or perform various operations in middleware. Cute Express maintains the order, executing middleware functions in the sequence they're defined.

But let's raise the stakes! How about middleware for specific routes?

Just like Express.js, Cute Express infuses middleware functions directly into your route declarations, creating a symphony of power and flexibility. Behold, the elegance of middleware in action:

```javascript
// Middleware for a specific route 
app.get('/profile', (req, res, next) => {
   console.log('Middleware for /profile activated.');
   next(); 
}, 
(req, res) => {
   res.send('Welcome to your profile!'); 
});
```

In this scenario, the middleware only activates when users venture into the `/profile` route.

## Conclusion

As you've seen, Cute Express has some fascinating features that I've introduced here. However, there's a lot more to uncover beyond what I've covered in this article.

To make sure you have an enjoyable experience and don't get overwhelmed, I've focused on showing you the basics.

But don't stop here!

Dive into Cute Express by exploring its [documentation](https://robiulhr.github.io/cute-express/). It's like a map that will guide you through all the exciting places within the framework.

If you ever have thoughts, ideas, or suggestions, I'd be thrilled to hear them. Your input could make Cute Express even better for everyone.

And guess what? If you're feeling brave and want to contribute to this project, you're invited! Whether you're a coding expert or just starting, your input is valuable.

So, go ahead and let your creativity flow. Cute Express is here to accompany you on your coding journey.

Have fun exploring, and happy coding!

* [Source code](https://github.com/robiulhr/cute-express)
    
* [npm package](https://www.npmjs.com/package/cute-express)