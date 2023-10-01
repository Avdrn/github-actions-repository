# CodeWomen workshop - Automate your deployment process with Github Actions

Welcome! This tutorial will guide you through the process of setting up a deployment pipeline with Github Actions from scratch, and help you grasp continuous integration and continuous delivery concepts (CI/CD) in practice.

Each lab introduces a new CI/CD concept and adds a new step to the pipeline. The initial labs will help you understand the tools and how to create a pipeline using Github Actions. By completing all the labs, you'll have a fully functional pipeline and a strong foundation in applying CI/CD principles to your projects.

&nbsp; &nbsp; 

## Who is it for?

This tutorial is designed for **programming students and junior developers or beginners in CI/CD**, who want to learn by doing and understand continuous delivery concepts and pipeline automation through hands-on practice.    

You don't need to have any previous experience in CI/CD but basic knowledge of Github commands is recommended.

&nbsp; &nbsp; 

## About the application

The **XXX** application is a [React](https://reactjs.org/)-Application bootstrapped with [Create React App](https://github.com/facebook/create-react-app) and tested with [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/).

#### Useful commands to build and run the application:

| Description                                               | Command         |
| --------------------------------------------------------- | --------------- |
| Installs all the dependencies listed in package.json      | `npm install`   |
| Builds the app for production to the `build` folder       | `npm run build` |
| Starts the app by deploy locally the app in dev mode      | `npm start`     |
| Runs the tests for the application                        | `npm test`      |
| Lint the Code with [ESLint](https://eslint.org/)          | `npm run lint`  |


&nbsp; &nbsp;   

## Getting Started 🚀

1. Anything you need for this workshop is contained within this repository - so the first thing you need to do is get a copy of it! If you are new to Github, you can learn how to **fork** it and **clone** it [here](https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository)
2. Make sure you start by the [Prerequisites section](docs/00-prerequisites.md) to make sure that you have everything we need installed
3. Run and build the React application following the instructions to [setup your application locally](docs/01-local-development.md) (lab 1)
4. Understand the basic use of GitHub Actions by [creating a hello world pipeline and running your first Github Action](docs/02-running-your-first-github-action.md) (lab 2)
5. Continue by creating a set of GitHub Actions workflows in order to [test](docs/03-adding-test-to-the-pipeline.md) (lab3), [release](docs/04-building-and-packaging-the-application.md) (lab 4) and [deploy](docs/05-deploying-to-an-environment.md) (lab 5) the application!


### Labs: 
These are the steps you can follow to complete this workshop (order is important):

- [Prerequisites](docs/00-prerequisites.md)
- [Lab 1 - Local development workflow](docs/01-local-development.md)
- [Lab 2 - Running your first Github Action to create a pipeline](docs/02-running-your-first-github-action.md)
- [Lab 3 - Continuous integration: Testing the application](docs/03-adding-test-to-the-pipeline.md)
- [Lab 4 - Continuous integration: Building and packaging the application](docs/04-building-and-packaging-the-application.md)
- [Lab 5 - Continuous delivery: Deploying the application to an environment](docs/05-deploying-to-an-environment.md)

&nbsp; &nbsp; 

## Resources - Learn More about CI/CD and Github Actions

- Continue practicing with this [Github Actions workshop](https://github.com/actions-workshop/actions-workshop)
