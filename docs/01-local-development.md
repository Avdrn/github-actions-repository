# Lab 1: Local development workflow

## 1.1 Installing the application dependencies
Once forked, you can navigate to the repository on your computer and install all project dependencies using:

```sh
cd github-actions-codewomen-workshop
npm install
```

## 1.2 Let's try our local development workflow

 `npm`, which is used in this workshop as a build tool, allows you to define automated build tasks in the package.json file. In this file you can see some build tasks already defined:

```javascript
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
  },
  ```

To build the app, we can just simple tell `npm `to do so.

```sh
npm run build
```

Our team is very professional and has written some unit tests to make sure we can refactor the application if needed. Lets make sure all of them are passing:

```sh
npm run test
```

If we want to deploy the app in the local environment in development mode, we can simple run:

```sh
npm start
```

and then open http://localhost:3000 to check our web app.

## Lab checklist

- [x] Read the instructions
- [ ] Install the app dependencies
- [ ] Build the application locally
- [ ] Run the unit tests locally
- [ ] Deploy the application locally in development mode