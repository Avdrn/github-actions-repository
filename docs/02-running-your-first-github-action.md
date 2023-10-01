# Lab 2: Running your first Github Action to create a CI/CD pipeline

### GitHub Actions to create a CI/CD pipeline

The goal of this tutorial is to understand the basic use of Github Actions creating a hello world pipeline.

The first step is to create a GitHub Workflow. Wait, what is a Github Workflow?    
Imagine GitHub Workflow as a set of instructions or a series of steps that automate processes in your software development projects on GitHub. These processes can include building your code, running tests, and deploying your application.

Ok! Now, let's get started. 

Open a terminal from the root of our project directory and create the following folder structure by running:

```
mkdir .github/
mkdir .github/workflows/
```

Navigate to the folder we just created:

```
cd .github/workflows/
```

Now we create a workflow inside the workflows folder:

```
touch pipeline.yml
```

The next step is to add the pipeline definition in the file we just created:

```yml
name: CI/CD Pipeline

on: push
jobs:
  hello-world:
    runs-on: ubuntu-latest
    steps:
      - name: Hello World step
        run: echo "Hello World!"
```

### Pipeline Core Concepts

- **_Name_**: This is just specifying a name for the workflow.
- **_On_**: The on command is used to specify an event that will trigger the workflow, this event can be push, pull_request, etc.
- **_Jobs_**: Here we are specifying the job we want to run, in this case, we are setting up a build job.
- **_Runs-on_**: is specifying the OS you want your workflow to run on.
- **_Steps_**: Steps just indicate the various steps you want to run on that job.

### Let's test our Pipeline

Once the changes are commited the pipeline should run automatically as especified to run on push.

```bash
git add .
git commit -m "Add workflow file"
git push
```


## Lab checklist

- [x] Read the instructions
- [ ] Create folder structure
- [ ] Create a github workflow
- [ ] Push the changes and check the pipeline execution in the Actions tab
