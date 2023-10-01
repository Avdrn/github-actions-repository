## Lab 5: Deployment with Firebase via Github Actions

### 5.1 Add Firebase setup:

#### Steps:
- Install the Firebase CLI if you haven’t already by running `npm install -g firebase-tools`    
- Sign up for a Firebase account and create a new project.     
- Run `firebase login:ci` and login with your previous created Firebase account.
- Copy token that appears in your console output
- Setup firebase in the project folder  run the `firebase init` command from your project’s root. It will show you the prompt and you need to select:     
-- Hosting: "Configure and deploy Firebase Hosting sites"    
-- “use an existing project” and choose the Firebase project you created in the previous step
-- agree with database.rules.json being created
-- choose "build" as the public directory     
-- agree to Configure as a single-page app by replying with y

#### Create firebase.yml

For this part, we will work directly from the web UI:    
- Open your Gihub repository in the browser: https://github.com/<YOUR-USERNAME>/github-actions-codewomen-workshop
- Click on "Actions" in the menu tabs on top    
- Search for node.js workflow and click Configure    
- Rename the file to `firebase.yml`
