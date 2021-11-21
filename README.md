# Tutorial: Deploying a basic Ionic Angular app on Jekyo

Demo app [here](https://ionic-angular-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Ionic Angular app

You can start your Ionic Angular project by using `jekyo create`

Using the **arrows** on your keyboard, select **ionic-angular** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ ionic-angular A basic starter app using [Ionic Angular](https://ionicframework.com/)
```
When prompted, enter the desired name for your Ionic Angular app. 

`Application name?: ionic-angular-tutorial`

This will create a basic Ionic Angular app in the current directory by cloning this [Ionic Angular starter app](https://github.com/jekyo/ionic-angular-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Ionic Angular app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd ionic-angular-tutorial`

Install dependencies:

```
npm install
```

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://ionic-angular-tutorial.jekyo.app ... OK
```

You can now browse to your Ionic Angular app on https://ionic-angular-tutorial.jekyo.app (replace 'ionic-angular-tutorial' with your app name)

## 2. Deploying an existing Ionic Angular app

Navigate to your local Ionic Angular app directory

`cd my-ionic-angular-app`

Initialize a git repository if you haven't already done so by running `git init`. 

### Edit package.json

In your **package.json** file, edit the **start** line under **scripts** to look like this: 

```
"start": "ng serve --host $HOST --port $PORT --disable-host-check",
```
This specifies necessary host and port variables for Jekyo and disables Angular's host-check.

[Commit](https://github.com/git-guides/git-commit) the new change:

```
git add package.json
git commit -m "modified start line in package.json"
```
Install dependencies:

```
npm install
```

### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-ionic-angular-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-ionic-angular-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-ionic-angular-app
```

### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-ionic-angular-app.jekyo.app ... OK
```

You can now browse to your Ionic Angular app on https://my-ionic-angular-app.jekyo.app (replace 'my-ionic-angular-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 
