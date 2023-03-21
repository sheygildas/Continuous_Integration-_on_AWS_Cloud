
# Project-06
## :ledger: Index

- [About The Project](#beginner-about-the-project)
- [Problem that this project solves ](#question-problem-that-this-project-solves)
- [Solution to the problem.](#key-solution-to-the-problem)
- [Tools](#hammer_and_wrench-Tools)
- [Architecture of this project](#house-architecture-of-this-project)
- [Steps to execute the project](#zap-steps-to-execute-the-project)
  - [Login to AWS Account ](#key-login-to-aws-account )
  - [Code Commit](#package-code-commit)
    - [Create CodeCommit repository](#package-create-codecommit-repository)
    - [Create IAM user with CodeCommit policy](#closed_lock_with_key-create-iam-user-with-codecommit-policy )
    - [Generate SSH keys locally](#key-generate-ssh-keys-locally)
    - [Exchange keys with IAM user](#key-exchange-keys-with-iam-user)
    - [Pull source code from github repository ](#package-pull-source-code-from-github-repository)
  - [Code Artifacte](#package-code-artifact)
    - [Create an IAM user with code artifact access](#closed_lock_with_key-create-an-iam-user-with-code-artifact-access)
    - [Install AWS CLI configure](#package-install-aws-cli-configure)
    - [Export authentication token](#key-export-authentication-token)
    - [Update settings.xml file in source code ](#package-update-settingsxml-file-in-source-code)
    - [Update pom.xml file with repository details](#package-update-pomxml-file-with-repository-details)
  - [Sonar cloud ](#cloud-sonar-cloud)
    - [Create sonar cloud account](#cloud-create-sonar-cloud-account)
    - [Generate token](#key-generate-token)
    - [Create SSM parameters with sonar details](#key-create-ssm-parameters-with-sonar-details)
    - [Create Build project](#rocket-create-build-project)
    - [Update CodeBuild role to access SSM parameter store](#key-update-codebuild-role-to-access-ssm-parameter-store)
  - [Create notifications for SNS or slack](#email-create-notifications-for-sns-or-slack)
  - [Build Project](#hammer_and_wrench-build-project)
    - [Update pom.xml with artifact version with timestamp](#package-update-pomxml-with-artifact-version-with-timestamp)
    - [Create variables in SSM parameter sore](#package-create-variables-in-ssm-parameter-sore)
    - [Create build project](#hammer_and_wrench-create-build-project)
    - [Update CodeBuild role to access SSM parameter store ](#key-update-codebuild-role-to-access-ssm-parameter-store)
  - [Create Pipeline](#package-create-pipeline)
    - [CodeCommit](#package-codecommit)
    - [Test code](#test_tube-test-code)
    - [Build](#hammer_and_wrench-build)
    - [Deploy to s3 bucket](#rocket-deploy-to-s3-bucket)
  - [Test Pipeline](#test_tube-test-pipeline)
- [Resources](#page_facing_up-resources)
- [Credit/Acknowledgment](#star2-creditacknowledgment)


## :beginner:About The Project

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :question: Problem that this project solves 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :key: Solution to the problem.

<<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Tools
- visual studio code
- AWS Account
- AWS CLI
- Maven
- JDK8 
- Sonar Cloud Account
- Git


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


## :beginner: Architecture of this project.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :zap: Steps to Execute the project. 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :key: Login to AWS Account

- Login into your AWS acount using the management console.
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>
### :package: Code Commit

- While signin in your AWS account, select `us-east-1` region aand search for CodeCommit service. 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Create CodeCommit repository

- Create CodeComit repository with the following name.

 ```sh
Name: vprofile-code-repo
   ```

- Follow the steps in the image below to configure you CodeComit reository so that you can connect to it through SSH.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create IAM user with CodeCommit policy

- Create an IAM user through console with CodeCommit access. We will create a policy for CodeCommit and allow full access only for `vprofile-code-repo`.
- Give the IAM user the following name.

```sh
Name: vprofile-code-admin-repo-fullaccess

   ```

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate SSH keys locally

-  Generate SSH keys locally using Git.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Exchange keys with IAM user
- Coppy the public SSH key that you generated Locally and upload it to your AM role Security credentials on AWS.

![Project Image](project-image-url)


- Next, create a config file locally using Git with the folowing details. SSH will use the config file to connect with CodeComit repo on AWS.

```sh
Host git-codecommit.us-east-1.amazonaws.com
    User <SSH_Key_ID_from IAM_user>
    IdentityFile ~/.ssh/vpro-codecommit_rsa

   ```
- Now, let's test our SSH connection to CodeCommit


```sh
ssh git-codecommit.us-east-1.amazonaws.com

   ```
   
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Pull source code from github repository 

- Clone the CodeComit repository to your local machine and take note of the location.
- Transition the `vprofile-project` repository from github to the CodeComit repository on AWS.
- Checkout the `vprofile-project` repository from github at this location [src/main/resources](https://github.com/sheygildas/Local_App_Setup/tree/local-setup/src/main/resources) directory.
- Run the following commands to do the transition.

```sh
git checkout master
git branch -a | grep -v HEAD | cur -d'/' -f3 | grep -v master > /tmp/branches
for i in `cat  /tmp/branches`; do git checkout $i; done
git fetch --tags
git remote rm origin
git remote add origin ssh://git-codecommit.us-east-1.amazonaws.com/v1/repos/vprofile-code-repo
cat .git/config
git push origin --all
git push --tags

   ```
   
- Now, the repo is ready on CodeCommit with all branches.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :package: Code Artifact

- While signin in your AWS account on the console, select `us-east-1` region aand search for Code Artifact service. 
- Create CodeArtifact repository with the following details, this CodeArtifact repository will be used by our Maven Build job.


 
```sh
Name: vprofile-maven-repo
Public upstraem Repo: maven-central-store
This AWS account
Domain name: visualpath

   ```
 
 - Follow the connection instructions given in CodeArtifact to create a connection with the `maven-central-repo`.

![Project Image](project-image-url)
 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create an IAM user with code artifact access

- Create an IAM user for CodeArtifact and configure aws CLI with its credentials of the IAM user. Also give the user programmatic access.

```sh
IAM name: vprofile-code-artifact-admin
IAM policy: AWSCodeArtifactAdminAccess

   ```
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Install AWS CLI configure

- Configure aws CLI with its IAM credentials.Install AWS CLI if you don't have it installed 

```sh
aws configure <provide your iam user credentials>
AWS Access key ID <>
AWS Secret key ID<>
Default region name <us-east-1>

   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Export authentication token

- Run command to get authentication token as in the Code Artifact instructions. 

```sh
export CODEARTIFACT_AUTH_TOKEN=`aws codeartifact get-authorization-token --domain visualpath --domain-owner 392530415763 --region us-east-1 --query authorizationToken --output text`

   ``` 
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update settings.xml file in source code 

- Update pom.xml and settings.xml with correct urls as suggested in instruction then push files to codeCommit.

- On your local machine, update the setting.xml file in our `vprofile-project` repository. change the following.

```sh
repository url: <replace it with your aws repo url found in the code artifact connection instruction>
domain name: <change it to your own domain name>
url below the domain name: <put a forward slash (/) at the end of the url>
   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml file with repository details

- Update pom.xml and pom.xml file with correct urls as suggested in instruction then push files to codeCommit.

- On your local machine, update the pom.xml file in our `vprofile-project` repository. change the following.

```sh
repository url: <replace it with your aws repo url found in the code artifact connection instruction>
   ```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


### :cloud: Sonar cloud 
- Set up a code analysis job using the sonar cloud. Folow the following steps to accomplish this task.


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :cloud: Create sonar cloud account

-  Go to https://www.sonarsource.com/products/sonarcloud/ and create an account if you have not done that yet.
<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate token

-  Sign in and go to -> `My Account` -> `Security`. Generate token name as `vprofile-sonartoken`. save the token somewhere on your machine.


![Project Image](project-image-url)

- Create a project, got to ->` Analyze Project` -> `create project manually`. 


```sh
ORGANIZATION          freedomthinker-projects	
HOST                  https://sonarcloud.io
PROJECT               vprofile-repo
SONARTOKEN            SecureString (put your sonarcloud token)
CODE ARTIFACT TOKEN   SecureString (put your token generated from aws cli)
```


<br/
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Create SSM parameters with sonar details
- Login to your AWS console and search for System Manager.
- Create parameters with the variables below which with obtain from sonar cloud.

```sh
Organization: freedomthinker-projects
Project key: vprofile-repo
```

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create Build project

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :email: Create notifications for SNS or slack

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Build Project

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml with artifact version with timestamp

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Create variables in SSM parameter sore

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Create build project

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Update CodeBuild role to access SSM parameter store 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :hole: Create Pipeline

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: CodeCommit

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :test_tube: Test code

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :hammer_and_wrench: Build

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :rocket: Deploy to s3 bucket

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :test_tube: Test Pipeline

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

## :page_facing_up: Resources

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


## :star2: Acknowledgment


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

