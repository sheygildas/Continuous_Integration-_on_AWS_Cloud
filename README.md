
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


Next, create a config file locally using Git with the folowing details. SSH will use the config file to connect with CodeComit repo on AWS.

```sh
Host git-codecommit.us-east-1.amazonaws.com
    User <SSH_Key_ID_from IAM_user>
    IdentityFile ~/.ssh/vpro-codecommit_rsa

   ```


<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Pull source code from github repository 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

### :package: Code Artifact

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :closed_lock_with_key: Create an IAM user with code artifact access

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Install AWS CLI configure

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Export authentication token

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update settings.xml file in source code 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :package: Update pom.xml file with repository details

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>


### :cloud: Sonar cloud 

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :cloud: Create sonar cloud account

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Generate token

<br/>
<div align="right">
    <b><a href="#Project-06">↥ back to top</a></b>
</div>
<br/>

#### :key: Create SSM parameters with sonar details

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

