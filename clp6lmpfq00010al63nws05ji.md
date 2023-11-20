---
title: "Deploy Vite React App on Both GitHub Pages and Vercel"
seoTitle: "Deploy Vite React App on Both GitHub Pages and Vercel"
seoDescription: "Have you ever wondered about deploying your React project on both GitHub Pages and Vercel simultaneously? Well, it's not just possible; it's super simple!"
datePublished: Mon Nov 20 2023 07:42:12 GMT+0000 (Coordinated Universal Time)
cuid: clp6lmpfq00010al63nws05ji
slug: deploy-vite-react-app-on-both-github-pages-and-vercel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700323955165/c6a12b37-7bbc-498d-9078-97180686e6b1.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1700326041565/477e7c85-7d92-416b-a458-eda40f534902.webp
tags: github, reactjs, vercel, github-actions-1, vite

---

Hey developers, hope you're doing great!

Have you ever wondered about deploying your React project on both GitHub Pages and Vercel simultaneously? Well, it's not just possible; it's super simple!

Now, you might be thinking, 'Why would I do that?'

Let's be real; in most cases, you won't deploy the same project on different servers. But, here's the twist. I've noticed something among beginner developers who showcase their practical projects on GitHub Pages or Vercel for their portfolio. Often, the shared link doesn't work smoothly, creating a not-so-great impression. Imagine having a backup deployment on another platform! It's a solution to avoid those awkward moments.

So, I'm here to guide you through deploying on both GitHub Pages and Vercel. It's not just a tech hack, it's an exploration! Join me, and let's dive in together.

Are you ready for the journey?

> Note: While there are multiple methods to create a React app, for the purpose of this guide, we'll be considering a React project using Vite, known for its speed and simplicity, which offers an efficient front-end build process. Although other approaches exist, we've chosen Vite for its ease of use. And for the routing, I am using react router dom.

All the code for this article is available on this [GitHub repository](https://github.com/robiulhr/deploy_react_app_github_pages_vercel). Feel free to check it out for a better understanding. Additionally, it can be used as a convenient template for kickstarting your React projects with GitHub Pages and Vercel. Feel free to fork, and utilize the code to enhance your development workflow.

## Deploy Vite React app to GitHub Pages

1. Begin by configuring the base URL in the vite.config.js file. This step is crucial because GitHub Pages uses a subdirectory-like URL structure for Project Pages. When hosted on GitHub Pages, a project is accessible at a link resembling `<ROOT>/project-name/`.  
      
    Define the base URL to match the project name to avoid errors and ensure your project can locate its assets correctly.  
      
    This is how the links should look like:
    
    ```markdown
    ❌ Bad 
    https://robiulhr.github.io/assets/favicon.17e50649.svg  
    ✅ Good 
    https://robiulhr.github.io/deploy_react_app_github_pages_vercel/assets/favicon.17e50649.svg   
    ```
    
    Update the vite.config.js file accordingly. Here project name is the name of our repository which means use the repo name as the base URL.
    
    ```javascript
    base: "/deploy_react_app_github_pages_vercel";
    ```
    
    after adding the base URL the `vite.config.js` file will look like this:
    
    ![set the base url of project in vite.config.js file](https://cdn.hashnode.com/res/hashnode/image/upload/v1700319425456/2a16aeef-316a-458a-85ae-dac1cbadcb73.png align="center")
    
2. Add a homepage field to your project’s package.json:
    
    ```json
    "homepage": "https://username.github.io/repo_name"
    ```
    
    Replace username with your GitHub username and repo\_name with your repository’s name.
    
3. Install gh-pages in your project:
    
    ```bash
    npm install --save gh-pages
    ```
    
    Modify your package.json scripts by adding these two scripts below:
    
    ```json
    "scripts": {    
       "predeploy": "npm run build",    
       "deploy": "gh-pages -d dist", 
     } 
    ```
    
    `predeploy` ensures the latest build is ready before deployment, and `deploy` triggers the deployment process.
    
4. Since we've included the base URL in the `vite.config.js` file as the repo name for deployment, we need to make adjustments in our React Router DOM setup. In your project's router setup, locate the part where you create the router using `createBrowserRouter`.
    
    As the second parameter of the createBrowserRouter method, add the following code:
    
    ```javascript
    const router = createBrowserRouter(routes, { basename: import.meta.env.BASE_URL });
    ```
    
    This line ensures that React Router DOM correctly handles the new base URL configuration.
    
    ![add basename to the roact router dom](https://cdn.hashnode.com/res/hashnode/image/upload/v1700319780447/a8f74d38-8f80-46c3-bc1c-588f9345576f.png align="center")
    
5. Execute the following command to deploy your application:
    
    ```bash
    npm run deploy
    ```
    
    This command creates a new branch named `gh-pages` in your GitHub repository.
    
6. Set the source branch to `gh-pages` in the GitHub Pages section of your repository’s settings.
    
    ![gh pages branch](https://cdn.hashnode.com/res/hashnode/image/upload/v1700320110764/c97ec05e-3b9c-4657-a476-9708ae3c31b2.png align="center")
    
    Navigate to Settings &gt; Pages to find the link to your deployed site.
    

### Automate Deployment using GitHub Actions

Manually deploying your project to GitHub Pages works, but wouldn't it be convenient if this process happened automatically with every push to the main branch?

GitHub Actions makes this automation easy. You can create workflows that specify the steps to build and deploy your React app whenever changes are pushed to the specified branch.

GitHub Actions work by defining workflows using YAML files in a `.github/workflows` directory in your repository. These workflows contain a set of jobs and steps that GitHub will run in response to events, such as pushes, pull requests, or manual triggers.

1. In your project repository, create a new folder named `.github/workflows` if it doesn't exist. Inside the `workflows` folder, create a new file named `deploy.yml`. This file will define your GitHub Actions workflow.
    
2. Paste the following YAML content into `deploy.yml`:
    
    ```yaml
    name: Deploy
    
    on:
      push:
        branches:
          - main
    
    jobs:
      build:
        name: Build
        runs-on: ubuntu-latest
    
        strategy:
          matrix:
            node-version: [16.x] # Specify the Node.js version you want to use
    
        steps:
          - name: Checkout repo
            uses: actions/checkout@v2
    
          - name: Setup Node
            uses: actions/setup-node@v3
            with:
              node-version: ${{ matrix.node-version }}
    
          - name: Install dependencies
            run: npm install
    
          - name: Build project
            run: npm run build
    
          - name: Upload production-ready build files
            uses: actions/upload-artifact@v2
            with:
              name: production-files
              path: ./dist
    
      deploy:
        name: Deploy
        needs: build
        runs-on: ubuntu-latest
        if: github.ref == 'refs/heads/main'
    
        steps:
          - name: Download artifact
            uses: actions/download-artifact@v2
            with:
              name: production-files
              path: ./dist
    
          - name: Deploy to GitHub Pages
            uses: peaceiris/actions-gh-pages@v3
            with:
              github_token: ${{ secrets.GITHUB_TOKEN }}
              publish_dir: ./dist
    ```
    
    This workflow consists of two jobs: build and deploy.
    
    The build job installs dependencies and builds the project, while the deploy job uses the action to deploy the contents of the `./dist` directory to GitHub Pages.
    
3. Commit the changes to your repository and push them to the main branch.
    
    ```bash
    git add .
    git commit -m "Add GitHub Actions workflow for automatic deployment"
    git push origin main
    ```
    
4. After running all the commands above, we can see our directory files on GitHub.
    
    In the repository, proceed to the [Actions](https://github.com/robiulhr/deploy_react_app_github_pages_vercel/actions/) tab. Click on the recent workflow.
    
    you might notice that it failed initially due to missing permissions.
    
    ![github workflow failed error](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321425593/829dcca8-b35c-4073-9582-928c11c8ddf8.png align="center")
    
    Since our action modifies the repository, it requires write permissions.
    
    To resolve this, Navigate to Actions Settings, Select Read and Write permissions, and Hit Save.
    
    ![setup workflow action on github](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321516844/aab62ab1-ed37-40bf-9f0c-218f3cabd9ac.png align="center")
    
    Now, check the status of your workflows. Go to Actions, and verify if the workflows have been executed successfully. If not, click on the failed workflow name. Inside the page, on the top-right section, you'll find an option to re-run the job.
    
    ![rerun failed workflow](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321598814/4c7fe7d3-99bb-4d9d-9e4e-39b2f0a2ed4e.png align="center")
    
    A successfully executed workflow will appear like this:
    
    ![check the workflow have executed successfully](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321653489/0180b57f-fa2f-411d-86cd-37caf663a24d.png align="center")
    
    Now, with every update to your project, GitHub Actions will automatically build and deploy your React project to GitHub Pages, keeping your live demo up to date.
    

## Deploy Vite react app on Vercel

1. To deploy your Vite React app on Vercel, begin by creating a new account. You can easily log in using OAuth.
    
    ![login vercel](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321957547/f4396c85-ce6b-4de1-bfc3-3a40efae2792.png align="center")
    
    Once logged in successfully, you'll land on the Vercel dashboard.
    
2. Import the project from the Git repository. If it's your first time using Vercel, you'll be prompted to install it for GitHub. Click "Install Now For GitHub" and follow the instructions. Save the settings for GitHub.
    
3. Navigate back to the [import Git](https://vercel.com/import/git) page, and you'll see that your GitHub is now connected. Click "Import Project from GitHub.".
    
4. If you haven't given permission for your GitHub repo click on the 'Adjust GitHub App Permissions' to provide the necessary permission. This will open a popup and from this popup select the repo you want to deploy to give the Repository access and click save.
    
5. Now you will see your selected project repo on the 'Import Git Repository' section.
    
    ![import project vercel](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322186275/1af83556-bd07-4072-919b-4d053b5a279c.png align="center")
    
    Click "Import" and you'll get a form to enter the project name, root directory, and Framework preset.
    
    ![new project vercel](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322304011/b9436647-6af3-49a9-a5b5-a808351e1c09.png align="center")
    
6. Make sure the Framework preset is selected as `vite` and the root directory is set to `./`.
    
7. Add an environment variable with the key as `VITE_BASE_PATH` and the value as `/`.  
    
    ![add environment variable](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322507376/c8213c37-92af-48c1-bd67-492e865da2f4.png align="center")
    
    You can name it anything, but ensure it starts with `VITE_` the preset. Leave other settings as default and click "Deploy."
    

Your React application will deploy within seconds, providing two to three preview links.

### Handle Base URL Dynamically

Even though we've completed the deployment process on Vercel, there's one more thing to address.

Since we've set the repository name as the basename in our `vite.config.js` file, we need to configure this dynamically. Otherwise, Vite will use the `/repo-name` URL instead of root URL `/`.

Inside the vite.config.js file, update the base URL with the following line:

```javascript
base: process.env.VITE_BASE_PATH || '/deploy_react_app_github_pages_vercel',
```

![dynamic base url inside vite.config.js file](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322993345/0b7d49db-0525-4c01-ab04-1b147e842357.png align="center")

With these changes, you've dynamically configured the base URL for your Vite React app on Vercel.

### Solve Client Side Routing issue on Vercel

After completing all the deployment steps, there's one more thing to address: making client-side routing work seamlessly on Vercel. Without this setup, if you navigate to a sub-route of your project and refresh the page, it won't work.

Let's fix this react router issue on Vercel by adding a configuration file.

* Add a file called `vercel.json` to the root directory of your project.
    

* Insert the following code into the `vercel.json` file:
    
    ```json
    {
      "rewrites": [
        {
          "source": "/(.*)",
          "destination": "/index.html"
        }
      ]
    }
    ```
    

This configuration ensures that all routes lead to index.html, enabling proper client-side routing.

> Note: As deployment processes on platforms like GitHub Pages and Vercel are subject to frequent updates, it's possible that the steps outlined here might differ when you execute them. If you encounter any difficulties deploying your project, kindly share the specific issues in the comments section.  
>   
> For the most current and detailed information, consult the official Vercel documentation for deploying Vite applications: [vite on vercel](https://vercel.com/docs/frameworks/vite)

With this setup, every time you push code to your repository, your project will be automatically deployed on both GitHub Pages and Vercel, providing a seamless and reliable deployment experience.

## Resources

* [8 ways to deploy a React app for free](https://blog.logrocket.com/8-ways-deploy-react-app-free)
    
* [Deploying Vite project to GitHub Pages](https://www.educative.io/answers/deploying-vite-project-to-github-pages)
    
* [Deploy Vite app to GitHub Pages using GitHub Actions](https://github.com/sitek94/vite-deploy-demo)