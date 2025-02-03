# Terraform Deployment in Jenkins

**PREQUISITIES**

- [***Docker Desktop***](https://larvariousmcdonald.atlassian.net/wiki/spaces/~712020d77bb1274bd44c7899751c7e766c2bee/pages/edit-v2/5767170#SIGN-UP-FOR-DOCKER-HUB-AND-INSTALL-DOCKER-DESKTOP) installed on your local machine
- [***Docker Container*** and ***Engine***](https://larvariousmcdonald.atlassian.net/wiki/spaces/~712020d77bb1274bd44c7899751c7e766c2bee/pages/edit-v2/5767170#STARTING-YOUR-DOCKER-CONTAINER-AND-ENGINE) up and running
- ***Jenkins Username and Password*** stored in your Notepad
- [***AWS IAM User & Credentials***](https://larvariousmcdonald.atlassian.net/wiki/spaces/~712020d77bb1274bd44c7899751c7e766c2bee/pages/edit-v2/5767170#INSERTING-AWS-CREDENTIALS-INTO-JENKINS-LOCALHOST) for Jenkins (Access Key & Secret Access Key)
- ***GitHub Repo with “Jenkinsfile“*** SAMPLE ([https://github.com/LarvariousM/JenkinsExperiment1](https://github.com/LarvariousM/JenkinsExperiment1))

### **SIGN UP FOR DOCKER HUB AND INSTALL DOCKER DESKTOP**

Sign up for sign in to docker hub - [https://hub.docker.com/](https://hub.docker.com/)

![1 - docker sign up or sign in.png](./attachments/1%20-%20docker%20sign%20up%20or%20sign%20in.png)

Create docker account - [https://app.docker.com/signup](https://app.docker.com/signup)

![2 - docker create account.png](./attachments/2%20-%20docker%20create%20account.png)

Install docker desktop - Windows = [https://docs.docker.com/desktop/setup/install/windows-install/](https://docs.docker.com/desktop/setup/install/windows-install/)

![3 - install docker desktop.png](./attachments/3%20-%20install%20docker%20desktop.png)

Install docker desktop - Mac [https://docs.docker.com/desktop/setup/install/mac-install/](https://docs.docker.com/desktop/setup/install/mac-install/)

![3.1 - install docker desktop on mac.png](./attachments/3.1%20-%20install%20docker%20desktop%20on%20mac.png)

Open Docker Desktop

![4 - open docker desktop.png](./attachments/4%20-%20open%20docker%20desktop.png)

Search for Jenkins in search bar, look for jenkins/jenkins, and pull

![5 - search for jenkins, jenkins jenkins and pull.png](./attachments/5%20-%20search%20for%20jenkins,%20jenkins%20jenkins%20and%20pull.png)

Open GitBash and run as administrator

![6- open gitbash run as admin.png](./attachments/6-%20open%20gitbash%20run%20as%20admin.png)

Type in this command to login to docker

```
docker login
```

![7 - docker login in gitbash.png](./attachments/7%20-%20docker%20login%20in%20gitbash.png)

Run this command in GitBash

```
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
```

Previous code creates new docker container for you

![8 - previous gitbash command creates new docker container.png](./attachments/8%20-%20previous%20gitbash%20command%20creates%20new%20docker%20container.png)

Click on Start button to start the docker containter.

Return to GitBash and run this command to login as root user, we need to find your password for further installation

```
docker exec -it --user root <your container name> bash
```

![10 - logged in as root user.png](./attachments/10%20-%20logged%20in%20as%20root%20user.png)

We need to navigate to this folder as root user to find our password.

```
ini/var/jenkins_home/secrets/initialAdminPassword
```

Once you find your password in this file, copy it and store it in your Notepad. It will look similar to this image below. ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f447.png)

```
206z1eacdc1d4ac1f1f565768za5f20G
```

Once you have your password ready, open up your favorite browser and enter [http://localhost:8080](http://localhost:8080) into the address bar

![0.4 jenkins localhost.png](./attachments/0.4%20jenkins%20localhost.png)

You will be brought to this next screen to Unlock Jenkins, enter your Administrator password you just put into your Notepad.

![11 - unlock jenkins.png](./attachments/11%20-%20unlock%20jenkins.png)

After putting in your Administrator password, you will brought to a webpage to create a User Name and Password for Jenkins. Go ahead and create one and store those also in your Notepad!

On the next page, the Customize Jenkins webpage. Choose 'Install suggested plugins'.

![12 - customize jenkins.png](./attachments/12%20-%20customize%20jenkins.png)

Suggested plugins will commence to installing.

![13 - getting started.png](./attachments/13%20-%20getting%20started.png)

Once all plugins have been installed, your Jenkins is ready!

![14 - jenkins is ready.png](./attachments/14%20-%20jenkins%20is%20ready.png)

### **STARTING YOUR DOCKER CONTAINER AND ENGINE**

Locate the ***Docker Desktop*** icon on your desktop and double click on it.

![0.1 Desktop Showing Docker Desktop.png](./attachments/0.1%20Desktop%20Showing%20Docker%20Desktop.png)

If Docker Desktop doesn’t load immediately on your screen, go to the bottom right hand side of your desktop and click the upwards arrow to show hidden icons running in the background of your computer, it will look like this.

![0.3 hidden icons.png](./attachments/0.3%20hidden%20icons.png)

Either double-click the Docker Desktop icon, or right-click the icon to bring up a prompt and click on GO TO DASHBOARD.

Once you’ve open Docker Desktop, the engine should automatically start running. ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f447.png)

![0.2 docker engine starting.png](./attachments/0.2%20docker%20engine%20starting.png)

Once the ***Docker Engine*** has started, you should be at your ***Docker Dashboard***. It should look like this image below ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f447.png)

![01 - Docker Desktop Installed On Computer.png](./attachments/01%20-%20Docker%20Desktop%20Installed%20On%20Computer.png)

Press The START Button under Actions to start your Docker Container

![01.2 - Press Start Button To Run Container.png](./attachments/01.2%20-%20Press%20Start%20Button%20To%20Run%20Container.png)

**\- Screenshot of Docker Engine running, and Docker Container running -**

### **LOGIN TO JENKINS LOCALHOST**

Now that we have Docker Engine and a Docker Container running simultaneously, we need to go to our Jenkins localhost, login and install some much needed plugins! ![(big grin)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/biggrin.png)

In order to do that, open up your favorite browser, and in the address bar type in [http://localhost:8080](http://localhost:8080)

![0.4 jenkins localhost.png](./attachments/0.4%20jenkins%20localhost.png)

After you’ve typed in [http://localhost:8080](http://localhost:8080), it should bring you to the glorious ***Jenkins Sign In Page***

![Jenkins Sign In.png](./attachments/Jenkins%20Sign%20In.png)

After you’ve signed in, it should bring you to the Jenkins Dashboard.

![0.6 jenkins localhost dashboard.png](./attachments/0.6%20jenkins%20localhost%20dashboard.png)

Now, we need to configure ***AWS Credentials*** into Docker. We’ll need to go to your AWS Account, go to IAM, Users, create a New User for Jenkins, and create new Access and Secret Access Keys.

Go to AWS Management Console, and click on Sign In ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f449.png)

 [https://aws.amazon.com/console/](https://aws.amazon.com/console/)

![aws login page.png](./attachments/aws%20login%20page.png)

Click on “Sign in using root user email“

![aws sign in with root user email.png](./attachments/aws%20sign%20in%20with%20root%20user%20email.png)

Once you’ve signed in to AWS using your email address, password, and MFA Authentication number( **If you don’t have a MFA Authentication setup yet, please do so right now or bad things will happen!**). It will bring you to the Console Homepage that looks like this!

![aws homepage.png](./attachments/aws%20homepage.png)

Either go to the Search bar up top and type in IAM, or click on under Recently visited.

![aws iam.png](./attachments/aws%20iam.png)

Click on Users, under Access management.

![aws users.png](./attachments/aws%20users.png)

Click on Create user.

![aws create user.png](./attachments/aws%20create%20user.png)

Give your username a crazy name you’ll never forget, make sure to not add any spaces unlike I did.

![aws add to usergroup.png](./attachments/aws%20add%20to%20usergroup.png)

Let’s add this new user to a group I’ve already created.

![aws create user 2.png](./attachments/aws%20create%20user%202.png)

Click on Create user.

![aws click on user.png](./attachments/aws%20click%20on%20user.png)

Click on the user you’ve just created.

![aws security credentials.png](./attachments/aws%20security%20credentials.png)

Click on Security credentials, we’ve got to give this user some ***G14 Classified*** assignments soon! ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f60e.png)

![aws create access key.png](./attachments/aws%20create%20access%20key.png)

Scroll down on the next page and click on Create Access Key, and it will bring you to this next page.

![05 - AWS - Secret Access Keys.png](./attachments/05%20-%20AWS%20-%20Secret%20Access%20Keys.png)

Click on Command Line Interface (CLI).

![06 - AWS Understand.png](./attachments/06%20-%20AWS%20Understand.png)

And choose, “I understand the above recommendation and want to proceed to create an access key.“, then click the Next button.

![07 - AWS.png](./attachments/07%20-%20AWS.png)

Click on create access key.

![](./attachments/08%20-%20Store%20Access%20&%20Secret%20Keys.png)

A new Access key and Secret access key will be created. Store your Access key and Secret Access Key in your Notepad on your PC, and never delete it! Unless you like Keisha or Lizzo!

### **INSERTING AWS CREDENTIALS INTO JENKINS LOCALHOST**

**Hey, are you still here with me? Are you okay? Just remember….everything is fine. We’re almost not halfway there. Just follow the Confluence!**

![Image20250107221920.gif](./attachments/Image20250107221920.gif)

Now, we’re going to add these AWS Credentials into our Jenkins localhost. Go back to your Jenkins Dashboard, and click on Manage Jenkins.

![09 - Go to Manage Jenkins to Install Plugins.png](./attachments/09%20-%20Go%20to%20Manage%20Jenkins%20to%20Install%20Plugins.png)

Under Security, click on Credentials.

![Jenkins Credentials.png](./attachments/Jenkins%20Credentials.png)

After you click on Credentials, under Domain, we’re going to hover over (global) and click on the drop down arrow, and select Add credentials.

![15 - Add Credentials.png](./attachments/15%20-%20Add%20Credentials.png)

Under Kind, change “Username with password“ to AWS Credentials.

![16 - Change Kind to AWS Credentials.png](./attachments/16%20-%20Change%20Kind%20to%20AWS%20Credentials.png)

In the ID field, you’re going to create a random ID, insert your AWS Access Key & Secret Access Key ID, and click the Create button. **Write down this random ID…you’re gonna need it later! TRUST ME**

![17 - Add AWS Credentials to Jenkins Credentials.png](./attachments/17%20-%20Add%20AWS%20Credentials%20to%20Jenkins%20Credentials.png)

### **INSTALLING PLUGINS TO JENKINS**

We need to install some plugins to Jenkins localhost to make this project work.

Here is the list of plugins to install:

1. AWS
2. AWS Credentials
3. Pipeline
4. Amazon EC2
5. Amazon Elastic Container Service
6. AWS Code Deploy
7. AWS Lambda
8. AWS S3 Bucket Credentials
9. AWS CodeBuild
10. AWS CodePipeline
11. AWS Secrets Manager Secret Source
12. Configuration as Code
13. CloudFormation
14. AWS SAM
15. Terraform
16. Google
17. Kubernetes
18. Google Cloud Storage
19. Google Cloud SDK
20. Pipeline
21. Snyk
22. SonarQube Scanner
23. Aqua - all 3
24. GitHub
25. GitHub Integration
26. GitHub Authentication
27. Pipeline GitHub
28. Pipeline GitHub Notify Step

![9 - Go to Manage Jenkins to Install Plugins.png](./attachments/9%20-%20Go%20to%20Manage%20Jenkins%20to%20Install%20Plugins.png)

1. Go to the dashboard in your Jenkins, and click on **Manage Jenkins**.

![10 - Go to Clouds.png](./attachments/10%20-%20Go%20to%20Clouds.png)

1. Click on **Clouds**, under System Configuration.

![11 - Install a plugin.png](./attachments/11%20-%20Install%20a%20plugin.png)

1. Under Clouds, click on **Install a plugin**

This page shows a list of all plugins to add to your Jenkins localhost, type in the name of each plugin and install each one.

![12 - Type in name of plugin.png](./attachments/12%20-%20Type%20in%20name%20of%20plugin.png)

Once you’re done adding all the plugins to the Jenkins localhost.

Now that we’ve configured our AWS Credentials into Jenkins and we’ve installed the necessary plugins, go back to your Jenkins Dashboard and select New Item.

![18 - Back to Dashboard, Create New Item.png](./attachments/18%20-%20Back%20to%20Dashboard,%20Create%20New%20Item.png)

Create a Item Name, select Create Pipeline, and click OK at the bottom of the page.

![19 - Create Pipeline.png](./attachments/19%20-%20Create%20Pipeline.png)

I’ve created an Item named 'whatever', it should bring you to a page like this. ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f447.png)

![new item.png](./attachments/new%20item.png)

Now we have to configure this Item, which is our Pipeline. So that we can run our terraform code stored in our GitHub repository. **You do still have that link, right?** ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f610.png)

 If so, click on the configure button.

![whatever - configure.png](./attachments/whatever%20-%20configure.png)

Scroll down this page until you see Pipeline, change the Definition from “Pipeline script“ to “Pipeline script from SCM“, but don’t SAVE just yet!

![20 - Pipeline script from SCM.png](./attachments/20%20-%20Pipeline%20script%20from%20SCM.png)

Under SCM, change “None“ to “Git“.

![scm - git.png](./attachments/scm%20-%20git.png)

Scroll down, under Repositories. Insert that GitHub repository from the top of this tutorial page into the Repository URL. Under Branch Specifier, change master to \*/master to \*/main. Scroll down to the bottom, and click on Save.

![](./attachments/git%20repository%20url%20&%20main%20branch.png)

Go to that GitHub Repository, fork it to your repositories. Then click on Jenkinsfile. We have to make some edits in that file for this Terraform deployment to work in Jenkins.

![github - jenkinsfile.png](./attachments/github%20-%20jenkinsfile.png)

Once you’ve selected the Jenkinsfile, click on the Pencil icon to edit the file.

![github edit file.png](./attachments/github%20edit%20file.png)

We’re going to edit Lines 11, 36, and 51 with our credentialsID we created in the Jenkins credentials, remember??? Also, Line 22 should point to the main branch in GitHub.

```
pipeline {
    agent any
    environment {
        AWS_REGION = 'us-east-1' 
    }
    stages {
        stage('Set AWS Credentials') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'INSERT JENKINS CREDENTIALS HERE' 
                ]]) {
                    sh '''
                    echo "AWS_ACCESS_KEY_ID: $AWS_ACCESS_KEY_ID"
                    aws sts get-caller-identity
                    '''
                }
            }
        }
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/LarvariousM/JenkinsExperiment1' 
            }
        }
        stage('Initialize Terraform') {
            steps {
                sh '''
                terraform init
                '''
            }
        }
        stage('Plan Terraform') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'INSERT JENKINS CREDENTIALS HERE'
                ]]) {
                    sh '''
                    export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID
                    export AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY
                    terraform plan -out=tfplan
                    '''
                }
            }
        }
        stage('Apply Terraform') {
            steps {
                input message: "Approve Terraform Apply?", ok: "Deploy"
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'INSERT JENKINS CREDENIALS HERE'
                ]]) {
                    sh '''
                    export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID
                    export AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY
                    terraform apply -auto-approve tfplan
                    '''
                }
            }
        }
    }
    post {
        success {
            echo 'Terraform deployment completed successfully!'
        }
        failure {
            echo 'Terraform deployment failed!'
        }
    }
}
```

Once you’re done making those changes, click on Commit Changes.

![github commit changes.png](./attachments/github%20commit%20changes.png)

Let’s go back to Jenkins localhost and build our first Pipeline. Go to your Item you’ve created, and click on Build Now.

![Jenkins buildnow.png](./attachments/Jenkins%20buildnow.png)

Click on the progress bar to show your current build in progress.

![jenkins build1.png](./attachments/jenkins%20build1.png)

Once you’ve clicked on the progress bar, it should bring you to the Console Output page. Scroll all the way down the page. I wanna show you some cool stuff, if you’ve been following the Confluence correctly! ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f60e.png)

![jenkins build2 console output.png](./attachments/jenkins%20build2%20console%20output.png)

My Terraform code has successfully INIT, VALIDATED, and PLANNED, and now wants my decision to Deploy 28 resources. Click on Deploy to build.

![jenkins build3 terraform deploy.png](./attachments/jenkins%20build3%20terraform%20deploy.png)

My Terraform Deployment in Jenkins is a success. We’ll also check in the AWS Console to verify the resources has been created.

![jenkins build4 success.png](./attachments/jenkins%20build4%20success.png)

Resources that were created in Amazon Web Services Console, from the Terraform Deployment in Jenkins.

![jenkins build5 awsconsoleproof.png](./attachments/jenkins%20build5%20awsconsoleproof.png)

Now let’s Terraform Destroy these resources from Git or PowerShell, whichever you choose. I’ll open up Git Bash, and run it as an Administrator.

![gitbash run as admin.png](./attachments/gitbash%20run%20as%20admin.png)

Once you’re in Git Bash, run this command.

```
docker exec -it --user root YOUR CONTAINER NAME bash
```

![gitbash enter this command to run as root user.png](./attachments/gitbash%20enter%20this%20command%20to%20run%20as%20root%20user.png)

Now, we have to cd aka Change Directory into the directory with terraform files. You can navigate the folders by using LS & CD commands. We have to navigate to the destination below: ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/1f447.png)

```
/var/jenkins_home/workspace/<PIPELINENAME>
```

As you can see on the screen,

cd → var, cd → jenkins\_home, cd → workspace, cd → pipelinename

![gitbash cd into your terraform project.png](./attachments/gitbash%20cd%20into%20your%20terraform%20project.png)

Now, you’re going to enter in your key information into GitBash.

```
export AWS_ACCESS_KEY_ID="YOUR ACCESS KEY"
export AWS_SECRET_ACCESS_KEY="YOUR SECRET ACCESS KEY"
export AWS_REGION="YOUR AWS REGION"
```

![gitbash enter aws credentials to destroy.png](./attachments/gitbash%20enter%20aws%20credentials%20to%20destroy.png)

Now, enter Terraform Destroy into GitBash.

You will be prompted to enter a value, Yes or No, to terraform destroy these resources. Enter ‘Yes’, unless you got Diddy money.

![gitbash enter value to destroy.png](./attachments/gitbash%20enter%20value%20to%20destroy.png)

Terraform Destroy Completed

![gitbash terraform destroy completed.png](./attachments/gitbash%20terraform%20destroy%20completed.png)

AWS Resource Gone!

![aws resources gone.png](./attachments/aws%20resources%20gone.png)

AWS Instances Terminated

![aws instances terminated.png](./attachments/aws%20instances%20terminated.png)

HOLD ON!!! WAIT! There’s one more thing! ![(blue star)](https://larvariousmcdonald.atlassian.net/wiki/s/-1852699047/6452/1ebf72ff01d8b09d243be3f04d6939608097a75e/_/images/icons/emoticons/72/2639.png)

 Let’s stop our Docker Container!

![docker stop container.png](./attachments/docker%20stop%20container.png)

Then, let’s pause our Docker Engine.

![docker stop engine.png](./attachments/docker%20stop%20engine.png)

Then, we can safely exit and close out Docker Desktop, but to be sure let’s Quit Docker Desktop. So, on your desktop click on show hidden icons on the bottom right-hand side of the screen. Right Docker Desktop, and let’s click on 'Quit Docker Desktop'.

![docker quit desktop.png](./attachments/docker%20quit%20desktop.png)

That concludes our tutorial for Deploying Terraform in Jenkins! That’s all folks!

![thats all folks.gif](./attachments/thats%20all%20folks.gif)