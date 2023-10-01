# CodeWomen workshop - Automate your deployment process with Github Actions

This tutorial will guide you through the process of setting up a deployment pipeline with Github Actions from scratch, and help you grasp continuous integration and continuous delivery concepts (CI/CD) practically.

Each exercise introduces a new CI/CD concept and adds a new step to the pipeline. The initial exercises will help you understand the tools and how to create a pipeline using Github Actions. By completing all the exercises, you'll have a fully functional pipeline and a strong foundation in applying CI/CD principles to your projects.

&nbsp; &nbsp; 

## Who is it for?

This tutorial is designed for programming students and junior developers or beginners in CI/CD, who want to learn by doing and understand continuous delivery concepts and pipeline automation through hands-on practice.    
You don't need to have any previous experience in CI/CD but basic knowledge of Github commands is recommended.

&nbsp; &nbsp; 

## Getting Started 🚀

1. Anything you need for this workshop is contained within this repository - so the first thing you need to do is get a copy of it! If you are new to Github, you can learn how to **fork** it and **clone** it [here](https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository)
2. Make sure you review the [pre-requisites section](#pre-requisites) below to make sure that you have everything we need installed
3. Start by building and running the application following the steps in the [application setup section](#application-setup)
4. Get started with exercise 1!

### Pre-requisites

This tutorial uses [npm](https://www.npmjs.com/) (Node Package Manager) as a build tool. Before you can run this project, you will need to:   

#### 1. Have `Node.js` installed in your computer
First check whether it is installed or not by running:
```
node -v
```
  - If Node.js is installed, this command will return the version number of Node.js that is installed on your system. 
  - If Node.js is not installed, the command will not be recognized, and you'll likely see an error message indicating that the command is not found. You can find instructions on [how to install Node.js](https://nodejs.org/en/download/) on the official website. 

#### 2. Download the latest version of `npm` on the command line
Same as before, you can first check if `npm` is installed by typing:
```
npm -v
```
- This command will return the version number of npm if it is installed on your system
- If you get an error indicating that the 'npm' command is not found, you can install `npm` by running the following command:
```
npm install -g npm
```
Re-run the previous command to check that it is now working:
```
npm -v
```

### Application Setup

The **XXX** application is a [React](https://reactjs.org/)-Application bootstrapped with [Create React App](https://github.com/facebook/create-react-app) and tested with React Testing Library.

#### Installing the application dependencies
Once forked, you can navigate to the repository on your computer and install all project dependencies using:

```sh
cd github-actions-codewomen-workshop
npm install
```

After that, you can start it in development mode to have a look at it:

```sh
npm start
```
and then open http://localhost:3000 to check our web app. The page will reload when you make changes.

### Other useful commands

| Description                                               | Command         |
| --------------------------------------------------------- | --------------- |
| Builds the app for production to the `build` folder.      | `npm run build` |
| Run Unit Tests with                                       | `npm run test`  |
| Lint the Code with [ESLint](https://eslint.org/)          | `npm run lint`  |

&nbsp; &nbsp; 

## Resources - Learn More about CI/CD and Github Actions

- Continue practicing with this [Github Actions workshop](https://github.com/actions-workshop/actions-workshop)
