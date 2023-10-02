# Lab 4: Continuous integration - Building and packaging the app

The goal of this lab is to show you how to add a stage in our pipeline to build and package the app.

## 4.1 - Adding a build stage to our continuous integration process

In the previous stage of our pipeline we make sure the latest changes are integrated and that the tests are passing. The next step is to build and package new version of the application.    

Wait, what? Let's review first some concepts: building and packaging an application refer to the process of compiling the source code of an application, along with any dependencies and assets, into a deployable format. This format could be an executable file, a package, or a container image, depending on the type of application and the target environment.

Now let's add a new job called `build` that will contain the following steps:

```yaml
jobs:
  [....]
  build:
    name: Build
    needs: test
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Setup Node.js ${{ env.NODE_VERSION }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ env.NODE_VERSION }}
      - name: Build the application
        run: |
          npm ci
          npm run build
      - name: Upload artifacts
        uses: actions/upload-artifact@v3
        with:
         name: react-app-v${{ github.sha }}
         path: build/
```

As you can see, we added a step to build the application and its dependecies with NPM. Finally, we use the upload-artifact Github Action to upload a build artifact that contains the code of the application.

> "Only build packages once. We want to be sure the thing we’re deploying is the same thing that we’ve tested throughout the deployment pipeline, so if a deployment fails we can eliminate the packages as the source of the failure." -- by [continuousdelivery.com](https://continuousdelivery.com/implementing/patterns/)


## 4.2 - Let's test our new pipeline stage

Once the changes are commited, the pipeline should run automatically as especified to run on push:

```bash
git add .
git commit -m "Add build stage to the CI pipeline"
git push
```

Now open you Github repo in the browser, click on the Actions tab and check the pipeline execution. It should look like this:

<img width="900" alt="image" src="https://github.com/caprosset/github-actions-repository/assets/12846321/7cc0068c-15d5-4c5e-8aa5-1030ad5f2671">


## Lab checklist

- [x] Read the instructions
- [ ] Add the build job to the CD workflow
- [ ] Push the changes and check the pipeline logs in the Actions tab
- [ ] Think about other tasks that could be automated as part of the build stage in the pipeline
