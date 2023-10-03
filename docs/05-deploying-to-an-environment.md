# Lab 5: Continuous delivery - Deploying the app with Firebase

The goal of this lab is to show you how you could automate the deployment of the app to a specific environment, e.g. staging or production.

## Adding a deployment stage to our continuous deployment pipeline

In previous stages of the pipeline we make sure the latest changes were integrated, the test were passing and the application is built and package. That gives us enough confidence that we can deploy the latest version of the application to an environment.

Think about it, when do the latest code changes start delivering value? Is it when they are tested and the application is built or is it when they are deployed and released to the end users?

This stage of the pipeline is a bit more complicated. So far we were running commands only in the Github Actions worker machines. To automate a deployment we need to trigger an action in an external service, the one providing the deployment environment. We need to authenticate with the service where we will deploy our app.

For the scope of this tutorial, we will use Firebase (a hosting service provided by Google). You can think of Firebase like a free server where you can expose your app to real users.    
If you don't have a Firebase account, it is fine! No worries. You can go for [option 1]() in this lab where we simulate a deployment.

> "Deploy the same way to every environment—including development. This way, we test the deployment process many, many times before it gets to production, and again, we can eliminate it as the source of any problems." -- by [continuousdelivery.com](https://continuousdelivery.com/implementing/patterns/)


## 5.1 - Option 1: Let's simulate a deployment

Let's start by adding a new build tasks to our package.json file. This task automates the process of performing a deployment to a specific environment. Your script section in the package.json file should look like:

```json
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "deploy:simulate": "../scripts/simulate-deployment.sh"
},
```

We added a new npm task, deploy:simulate, that calls a script that simulates a deployment and tells when the deployment is completed.     
Let's try to execute the automated deployment process locally and see what happens. 

```bash
npm run deploy:simulate -- production
```

If you get error "sh: scripts/simulate-deployment.sh: Permission denied", run the following command in the terminal:
```bash
chmod +x scripts/simulate-deployment.sh 
```
and again the previous one.

### Adding a deployment stage to our continuous delivery proces

So far so good, we automated our deployment process so that we can run it from our local environment. Next step is to perform the automated deployment as part of the pipeline. Lets add a new job that allow us to deploy our modern web app to an environment that we will call production. Lets add a new job:

```yaml
jobs:
    [....]
    deploy-prod:
      name: Deploy to prod
      needs: build
      runs-on: ubuntu-latest
      steps:
        - name: Checkout code
          uses: actions/checkout@v2
        - name: Deploy with Node.js ${{ env.NODE_VERSION }}
          uses: actions/setup-node@v1
          with:
            node-version: ${{ env.NODE_VERSION }}
        - name: Download build artifact
          uses: actions/download-artifact@v3
          with:
            name: react-app-${{ github.sha }}
            path: build
        - name: Deploy to prod environment
          run: |
           npm run deploy:simulate -- production
```

### Let's test our new pipeline stage

Once the changes are commited and pushed, the pipeline should run automatically as it is especified to run on push.

```bash
git add .
git commit -m "Add deployment simulation stage to the CI/CD pipeline"
git push
```

&nbsp; &nbsp; 

## 5.2 - Option 2: Let's perform a real deployment with Firebase

### First, add Firebase setup:

- Install the Firebase CLI if you haven’t already by running `npm install -g firebase-tools`    
- [Sign up](https://console.firebase.google.com/) for a Firebase account and create a new project     
- Run `firebase login:ci` in the terminal and login with your previous created Firebase account
- Copy token that appears in your console output

Next we need to setup firebase in the project folder:   
- run the `firebase init` command from your project’s root. It will show you the prompt and you need to select:
  -- Hosting: “Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys”
  -- “use an existing project” and choose the Firebase project you created in the previous step
  -- agree with database.rules.json being created
  -- choose "build" as the public directory
  -- select no to the question rewrite all the urls
  -- select no for all the other questions

Now you should see the new file called `firebase.json` with some settings, as well as the `.firebaserc` file in the root folder of our project.

Commit and git push:
```bash
git add .
git commit -m "Add firebase setup"
git push
```

### Adding a deployment stage to our continuous delivery process

Lets add a new job that allow us to deploy our app to an environment that we will call production.

```yaml
jobs:
  [...]
  deploy-prod:
    name: Deploy to prod
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Deploy with Node.js ${{ env.NODE_VERSION }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ env.NODE_VERSION }}
        - name: Download build artifact
          uses: actions/download-artifact@v3
          with:
            name: react-app-${{ github.sha }}
            path: build
      - name: Deploy to prod environment on Firebase
        uses: w9jds/firebase-action@master
        with:
          args: deploy --only hosting
        env:
          FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
```

### Let's test our new pipeline stage

Once the changes are commited and pushed, the pipeline should run automatically as it is especified to run on push.

```bash
git add .
git commit -m "Add Firebase deployment stage to the CI/CD pipeline"
git push
```

The pipeline should now fail because of missing Firebase token. Let's fix it!
In the repo settings, go to 'Secrets and variables' > 'Actions' and create a new repository secret. Call it `firebase token` and paste the token value that you got during the Firebase setup. Click 'add secret'.

<img width="900" alt="image" src="https://github.com/caprosset/github-actions-repository/assets/12846321/78021ed9-400f-41f7-9aee-c5cd717f577d">

<img width="900" alt="image" src="https://github.com/caprosset/github-actions-repository/assets/12846321/b0b644f5-674d-449e-b88f-a0fe6a833b2e">

Commit the changes and see the pipeline pass!

&nbsp; &nbsp; 

## Lab checklist

- [x] Read the instructions
- [ ] Add the deploy: simulate deployment tasks in the NPM scripts declaration
- [ ] Add the automated deployment job to the CD pipeline
- [ ] Push the changes and check the pipeline logs in the Actions tab
- [ ] Answer this question: is the pipeline implementing continuous delivery or continuous deployment?
