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
4. Understand the basic use of GitHub Actions by [creating your first pipeline](docs/02-creating-your-first-github-workflow.md) (lab 2)
5. Continue by creating a set of GitHub Actions workflows in order to [test](docs/03-adding-test-to-the-pipeline.md) (lab3), [release](docs/04-building-and-packaging-the-application.md) (lab 4) and [deploy](docs/05-deploying-to-an-environment.md) (lab 5) the application!


### Labs: 
These are the steps you can follow to complete this workshop (order is important):

- [Prerequisites](docs/00-prerequisites.md)
- [Lab 1 - Local development workflow](docs/01-local-development.md)
- [Lab 2 - Creating a hello-world pipeline](docs/02-creating-your-first-github-workflow.md)
- [Lab 3 - Continuous integration: Testing the application](docs/03-adding-test-to-the-pipeline.md)
- [Lab 4 - Continuous integration: Building and packaging the application](docs/04-building-and-packaging-the-application.md)
- [Lab 5 - Continuous delivery: Deploying the application to an environment](docs/05-deploying-to-an-environment.md)


&nbsp; &nbsp; 

## Useful Theory

[What is a pipeline?](https://www.atlassian.com/devops/devops-tools/devops-pipeline#:~:text=A%20DevOps%20pipeline%20is%20a,code%20to%20a%20production%20environment.)
A pipeline is a system of automated processes designed to quickly and accurately move new code additions and updates from version control to production.

[What is continous integration?](https://martinfowler.com/articles/continuousIntegration.html#:~:text=Continuous%20Integration%20is%20a%20software,to%20multiple%20integrations%20per%20day.)
Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily - leading to multiple integrations per day.

[What is continous delivery?](https://aws.amazon.com/devops/continuous-delivery/?nc1=h_ls)
is a software development practice where code changes are automatically prepared for a release to production.
With continuous delivery, every code change is built, tested, and then pushed to a non-production testing or staging environment.
Continuous delivery automates the entire software release process.

[What are the differences between continuous integration vs. delivery vs. deployment?](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment)

[What is continuous testing?](https://continuousdelivery.com/foundations/test-automation/)
Continuous testing is the practice of running many different types of tests—both manual and automated—continually throughout the delivery process with the goal of finding problems as soon as possible.

[What is test automation?](https://www.atlassian.com/devops/devops-tools/test-automation)
Test automation is the practices of automating test tasks to make sure the application is ready to be deployed and it meets the pre-defined quality standards.

[What is Github Actions?](https://resources.github.com/downloads/What-is-GitHub.Actions_.Benefits-and-examples.pdf)
GitHub Actions brings automation directly into the software development lifecycle on GitHub via event-driven triggers. These
triggers are specified events that can range from creating a pull request to building a new brand in a repository.

[Github Actions Docs](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions?learn=getting_started)


&nbsp; &nbsp; 

## Additional resources

- Continue practicing with this [Github Actions workshop](https://github.com/actions-workshop/actions-workshop)
