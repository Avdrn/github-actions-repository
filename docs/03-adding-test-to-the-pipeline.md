# Lab 3: Continuous integration - Testing the app

The goal of this lab is to create the first stage in our CD pipeline, the test step. We will use what we learnt in lab 2 and replace our hello world pipeline for something more useful.

## 3.1 - Adding a testing stage to our continuous integration process

First we need to specify which version of Node.js we eill need. We can do that by declaring an environment variable that we can reference later on.

```yml
env:
  NODE_VERSION: "14.17"
```

The next step is to simply specify the test job and add it to the pipeline definition:

```yml
jobs:
  test:
    name: Test
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Setup Node.js ${{ env.NODE_VERSION }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ env.NODE_VERSION }}
      - name: Run unit tests
        run: |
          npm ci
          npm run test
```

### Pipeline Concepts

- **_env_**: To specify environment variables that can be reused across the pipeline definition.
- **_uses_**: To specify already defined GH Actions. You can think of these as reusable actions that you can incorporate in your pipeline, e.g. checkout, setup-node...
- **_with_**: To pass parameters to already defined GH Actions.

## 3.2 - Let's test our new pipeline stage

Once the changes are commited and pushed, the pipeline should run automatically as it is especified to run on push.

```bash
git add .
git commit -m "Add test stage to the CI pipeline"
git push
```

Now check the pipeline execution in the Actions tab. It should look like this:

<img width="900" alt="image" src="https://github.com/caprosset/github-actions-repository/assets/12846321/5a448c54-004d-48fe-95c3-b5401480c075">

## 3.3 - Fix the tests and see the pipeline pass

The pipeline failed because one of our tests was failing!
In the src/App.test.js file, change line 7 by:
```javascript
expect(linkElement).toBeInTheDocument();
```

Commit and push the changes:
```bash
git add .
git commit -m "Fix test"
git push
```

Go back to the pipeline execution in the Actions tab. It should now look like this:

<img width="900" alt="image" src="https://github.com/caprosset/github-actions-repository/assets/12846321/93d20de8-d1fb-4a1c-9835-81be0a9a1e58">

## Lab checklist

- [x] Read the instructions
- [ ] Replace the hello world job with the new test job
- [ ] Push the changes and check the pipeline execution in the Actions tab
- [ ] Fix the test, commit and push the changes. Check what happens.
