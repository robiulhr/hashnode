---
title: "PM2: A Journey from Basics to Advanced Node.js Process Management"
seoTitle: "PM2: A Journey from Basics to Advanced Node.js Process Management"
seoDescription: "PM2 is a production-grade process manager for Node.js applications. It is designed to help manage, monitor, and keep applications running continuously."
datePublished: Thu Nov 14 2024 01:41:30 GMT+0000 (Coordinated Universal Time)
cuid: cm3gn9i6x000009mse28d9ckb
slug: pm2-a-journey-from-basics-to-advanced-nodejs-process-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1731546921739/a0fb7d8d-ff4d-4e99-aa41-0f8655d017db.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1731546937410/e1442c2a-e0f4-489a-befe-8f5cc158ab7a.webp
tags: express, javascript, mongodb, nodejs, reactjs, pm2, mern, nextjs

---

Welcome to your journey with [PM2](https://pm2.keymetrics.io/), the powerful process manager for Node.js applications. Whether you're a beginner just starting with Node.js or an experienced developer looking to optimize your application management, this guide will walk you through PM2 from the ground up. We'll focus primarily on managing a MERN ([MongoDB](https://www.mongodb.com/), Express, React, Node.js) stack application, but the principles apply to any Node.js project.

Ok, before discussing other things. Let’s answer the main question that you may have in your mind and that is - **What is PM2**?

**PM2** is a production-grade process manager for Node.js applications. It is designed to help manage, monitor, and keep applications running continuously. PM2 provides features such as automatic application restarts on failure, and comprehensive log management. This tool simplifies the deployment and management of Node.js applications by enabling efficient resource use and ensuring high availability, making it especially useful for managing web servers, APIs, and complex Node.js services in production environments.

## Step 1: Installing PM2

Let's begin our journey by installing PM2. Open your terminal and run:

```bash
npm install -g pm2
```

This command installs PM2 globally on your system, making it available for all your projects.

## Step 2: Running Your First Node.js File with PM2

Let's start with a simple Node.js file. Create a file named `app.js` with the following content:

```js
console.log('Hello, PM2!');
setInterval(() => {
    console.log("'I'm still running!");
}, 5000);
```

Now, let's run this file with PM2:

```bash
pm2 start app.js
```

Congratulations! You've just started your first process with PM2.

## Step 3: Running npm Scripts with PM2

As your projects grow more complex, you'll often use npm scripts defined in your `package.json` file to start your application. PM2 can manage these scripts just as easily as it manages individual files.

Let's use a Next.js application as an example:

1. First, ensure your `package.json` has a start script. For a Next.js app, it typically looks like this:
    

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  }
}
```

2. To run the production version of your Next.js app with PM2, use the following command:
    

```bash
pm2 start npm --name "next-app" -- start
```

This tells PM2 to run the `npm start` command, which in turn runs `next start` for a Next.js application.

* `pm2 start npm`: Runs the `npm` command using PM2.
    
* `--name "next-app"`: Names the process for easy identification.
    
* `-- start`: Passes `start` as an argument to `npm`, ensuring that `npm` runs the `start` script defined in your `package.json`.
    

3. If you want to run the development version, you can use:
    

```bash
pm2 start npm --name "next-app-dev" -- run dev
```

This runs `npm run dev`, which starts the Next.js development server.

4. You can apply the same principle to other npm scripts. For example, if you have a custom script called `server`:
    

```bash
pm2 start npm --name "custom-server" -- run server
```

This approach is not limited to Next.js. You can use it with any [Node.js](https://nodejs.org/en) application that uses [npm](https://www.npmjs.com/) scripts, such as Express.js servers, React applications, or even custom Node.js scripts.

## Step 4: Managing Multiple npm Scripts

For complex projects with multiple components, such as a [MERN](https://www.simplilearn.com/tutorials/mongodb-tutorial/what-is-mern-stack-introduction-and-examples) (MongoDB, Express, [React](https://react.dev/), Node.js) stack application, you'll often need to manage several npm scripts simultaneously. PM2's ecosystem file feature is perfect for this scenario, allowing you to define and manage multiple processes in a single configuration file.

Create a file named `ecosystem.config.js` in your project root. This file will define all the processes PM2 should manage. Here's an expanded example:

```js
module.exports = {
  apps: [
    {
      name: "next-app",
      script: "npm",
      args: "start",
      cwd: "./frontend",
      env: {
        NODE_ENV: "production",
        PORT: 3000
      },
      env_development: {
        NODE_ENV: "development",
        PORT: 3000
      }
    },
    {
      name: "express-server",
      script: "npm",
      args: "run server",
      cwd: "./backend",
      env: {
        NODE_ENV: "production",
        PORT: 5000
      },
      env_development: {
        NODE_ENV: "development",
        PORT: 5000
      }
    },
  ]
}
```

Let's break down the configuration options:

* `name`: A unique identifier for each process.
    
* `script`: The command to run. Use `"npm"` for npm scripts.
    
* `args`: Arguments to pass to the script. For npm scripts, use `"start"`, `"run server"`, etc.
    
* `cwd`: The working directory for the process. Useful when your frontend and backend are in separate directories.
    
* `env`: Environment variables for production.
    
* `env_development`: Environment variables for development.
    

To start all processes defined in your ecosystem file:

```bash
pm2 start ecosystem.config.js
```

To start processes in development mode:

```bash
pm2 start ecosystem.config.js --env development
```

This approach gives you the flexibility to manage complex applications with multiple components, all through PM2.

## Step 5: Basic PM2 Commands

Now that we have a process running, let's learn some basic PM2 commands:

1. List running processes:
    

```bash
pm2 list
```

2. Stop a specific process::
    

```bash
pm2 stop next-app
```

3. Restart a specific process:
    

```bash
pm2 restart next-app
```

4. Delete a specific process from PM2:
    

```bash
pm2 delete next-app
```

5. Stop all processes:
    

```bash
pm2 stop all
```

6. Restart all processes:
    

```bash
 pm2 restart all
```

7. Delete all processes:
    

```bash
pm2 delete all
```

## Step 6: Monitoring Your Application

1. PM2 provides a real-time monitoring tool. Try it out:
    

```bash
pm2 monit
```

This command opens an interface where you can see CPU usage, memory consumption, and logs for your running processes.

2. Display process details:
    

```bash
pm2 show next-app
```

This command provides detailed information about a specific process, including its configuration, metadata, and recent logs.

## Step 7: Reloading Without Downtime

To update your application with zero downtime:

```bash
pm2 reload ecosystem.config.js
```

This command gracefully reloads all processes defined in your ecosystem file, ensuring that your application remains available during updates.

## Step 8: Managing Logs

Logs are crucial for understanding what's happening in your application. Here's how to view them:

1. View logs:
    

```bash
pm2 logs
```

2. View logs for a specific application:
    

```bash
pm2 logs next-app
```

3. Clear log files:
    

```bash
pm2 flush
```

4. To view only error logs:
    

```bash
pm2 logs --err
```

## **Step 9: Automatic Restart on Crashes**

One of PM2's most powerful features is its ability to automatically restart applications that crash or stop unexpectedly. This feature ensures high availability and reliability for your Node.js applications.

Here's how it works:

1. PM2 constantly monitors the processes it manages.
    
2. If a process crashes or exits with an error code, PM2 will automatically restart it.
    
3. This happens without any manual intervention, minimizing downtime.
    

Here are some key options that allow you to fine-tune the automatic restart behavior. These options can be added to your `ecosystem.config.js` file or specified when starting an application.

1. `max_restarts`: Sets the maximum number of restarts within a time frame.
    
2. `min_uptime`: Minimum uptime of the app to be considered started.
    
3. `max_memory_restart`: Restarts the app if it exceeds a specified memory limit.
    
4. `restart_delay`: Delay between automatic restarts (in milliseconds).
    
5. `autorestart`: Enables or disables the automatic restart feature.
    

Let's update the `ecosystem.config.js` file to include these options:

```javascript
module.exports = {
  apps: [{
    name: "my-app",
    script: "app.js",
    max_restarts: 10,
    min_uptime: "5s",
    max_memory_restart: "200M",
    restart_delay: 4000,
    autorestart: true
  }]
}
```

In this configuration:

* The app will restart a maximum of 10 times.
    
* The app must run for at least 5 seconds to be considered successfully started.
    
* If the app uses more than 200MB of memory, it will be restarted.
    
* There will be a 4-second delay between restarts.
    
* Automatic restarts are enabled (this is the default, but we're explicitly setting it here).
    

You can also set these options when starting an app from the command line:

```bash
pm2 start app.js --max-restarts 10 --min-uptime 5000 --max-memory-restart 200M --restart-delay 4000
```

### Example: Demonstrating Automatic Restart

Let's create a simple Node.js application that will crash periodically to demonstrate PM2's automatic restart feature.

1. Create a new file named `crash-test.js` with the following content:
    
    ```javascript
    let count = 0;
    
    setInterval(() => {
      console.log(`Running for ${count} seconds`);
      count++;
    
      if (count % 10 === 0) {
        console.log("Simulating a crash...");
        throw new Error("Application crashed!");
      }
    }, 1000);
    ```
    
    This script will run for 10 seconds and then simulate a crash by throwing an error.
    
2. Create an `ecosystem.config.js` file with the following content:
    
    ```javascript
    module.exports = {
      apps: [{
        name: "crash-test",
        script: "crash-test.js",
        max_restarts: 5,
        min_uptime: "3s",
        restart_delay: 2000
      }]
    }
    ```
    
3. Start the application with PM2:
    
    ```bash
    pm2 start ecosystem.config.js
    ```
    
4. Monitor the application:
    
    ```bash
    pm2 monit
    ```
    
    You'll see in the monitoring interface that every 10 seconds, the application crashes and PM2 automatically restarts it, with a 2-second delay between restarts.
    
5. To view the logs and see the crash and restart events:
    
    ```bash
    pm2 logs crash-test
    ```
    
    You'll see output similar to this:
    
    ```bash
    0|crash-test  | Running for 8 seconds
    0|crash-test  | Running for 9 seconds
    0|crash-test  | Simulating a crash...
    0|crash-test  | Error: Application crashed!
    0|crash-test  |     at Timeout._onTimeout (/path/to/crash-test.js:8:11)
    0|crash-test  |     at listOnTimeout (node:internal/timers:559:17)
    0|crash-test  |     at processTimers (node:internal/timers:502:7)
    PM2        | App [crash-test:0] exited with code [1] via signal [SIGINT]
    PM2        | App [crash-test:0] starting in -fork mode-
    0|crash-test  | Running for 0 seconds
    0|crash-test  | Running for 1 seconds
    ```
    

This example demonstrates how PM2 automatically restarts your application when it crashes, ensuring continuous operation even in the face of unexpected errors. The configuration options we've set limit the number of restarts to 5 and introduce a 2-second delay between restarts, helping to prevent rapid restart loops in case of persistent issues.

## Real-world Example: MERN Stack

Here's how you might set up an ecosystem file for a typical MERN stack application:

```js
module.exports = {
  apps: [
    {
      name: "react-frontend",
      script: "npm",
      args: "start",
      cwd: "./client",
      env: {
        NODE_ENV: "production",
        PORT: 3000
      }
    },
    {
      name: "express-backend",
      script: "npm",
      args: "run server",
      cwd: "./server",
      env: {
        NODE_ENV: "production",
        PORT: 5000,
        MONGODB_URI: "mongodb://localhost:27017/myapp"
      }
    },
    {
      name: "mongodb",
      script: "mongod",
      args: "--port 27017"
    }
  ]
}
```

This configuration starts a React frontend, an [Express.js](https://expressjs.com/) backend, and a MongoDB instance, all managed by PM2.

By leveraging PM2's ecosystem files, you can efficiently manage complex, multi-component applications, ensuring all parts of your stack start together and are monitored effectively. This approach simplifies deployment, improves maintainability, and gives you fine-grained control over each component of your application.

## Conclusion

Congratulations! You've completed your journey from PM2 basics to advanced usage. You've learned how to start simple scripts, manage complex applications, handle logs, use environment variables, and even tackle a full MERN stack. Remember, PM2 is a powerful tool with many more features to explore. As you continue your development journey, don't hesitate to dive into the PM2 documentation for more advanced usage and optimizations.

Happy coding, and may your applications always stay up and running with PM2!