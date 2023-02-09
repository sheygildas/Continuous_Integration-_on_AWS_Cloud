
# Project-03
## :ledger: Index

- [About The Project](#beginner-about-the-project)
- [Problem that this project solves ](#question-problem-that-this-project-solves)
- [Solution to the problem.](#key-solution-to-the-problem)
- [Tools](#hammer_and_wrench-Tools)
- [Architecture of this project](#house-architecture-of-this-project)
- [Steps to execute the project](#zap-steps-to-execute-the-project)
  - [Login to AWS Account ](#key-login-to-aws-account )
  - [Code Commit](#closed_lock_with_key-create-key-pairs)
  - [Create CodeCommit repository](#lock-create-security-groups)
  - [Create IAM user with CodeCommit policy](#bulb-launch-instances-with-user-data )
  - [Generate SSH keys locally](#earth_africa-update-ip-to-name-mapping-in-route-53)
  - [Exchange keys with IAM user](#hammer_and_wrench-build-application-from-source-code)
  - [Pull source code from github repository ](#rocket-upload-to-S3-bucket)
  - [Code Artifacte](#package-download-artifact-to-tomcat-ec2-instance)
  - [Create an IAM user with code artifact access](#lock-setup-elb-with-https )
  - [Install AWS CLI, configure](#earth_africa-map-elb-endpoint-to-website-name-in-dns)
  - [Export authentication token](#hammer_and_wrench-build-autoscaling-group-for-tomcat-nstances)
  - [Code Commit](#closed_lock_with_key-create-key-pairs)
  - [Update settings.xml file in source code ](#closed_lock_with_key-create-key-pairs)
  - [Update pom.xml file with repository details](#closed_lock_with_key-create-key-pairs)
  - [Sonar cloud ](#closed_lock_with_key-create-key-pairs)
  - [Create sonar cloud account](#closed_lock_with_key-create-key-pairs)
  - [Generate token](#closed_lock_with_key-create-key-pairs)
  - [Create SSM parameters with sonar details](#closed_lock_with_key-create-key-pairs)
  - [Create Build project](#closed_lock_with_key-create-key-pairs)
  - [Update CodeBuild role to access SSM parameter store](#closed_lock_with_key-create-key-pairs)
  - [Create notifications for SNS or slack](#closed_lock_with_key-create-key-pairs)
  - [Build Project](#closed_lock_with_key-create-key-pairs)
  - [Update pom.xml with artifact version with timestamp](#closed_lock_with_key-create-key-pairs)
  - [Create variables in SSM parameter sore](#closed_lock_with_key-create-key-pairs)
  - [Create build project](#closed_lock_with_key-create-key-pairs)
  - [Update CodeBuild role to access SSM parameter store ](#closed_lock_with_key-create-key-pairs)
  - [Create Pipeline](#closed_lock_with_key-create-key-pairs)
  - [CodeCommit](#closed_lock_with_key-create-key-pairs)
  - [Test code](#closed_lock_with_key-create-key-pairs)
  - [Build](#closed_lock_with_key-create-key-pairs)
  - [Deploy to s3 bucket](#closed_lock_with_key-create-key-pairs)
  - [Test Pipeline](#closed_lock_with_key-create-key-pairs)
- [Resources](#page_facing_up-resources)
- [Credit/Acknowledgment](#star2-creditacknowledgment)


## :beginner:About The Project

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :question: Problem that this project solves 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :key: Solution to the problem.

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :hammer_and_wrench: Tools
- A tool
- B tool

| Name | Description |
| --- | --- |
| [`@toast-ui/editor-plugin-chart`](https://github.com/nhn/tui.editor/tree/master/plugins/chart) | Plugin to render chart |
| [`@toast-ui/editor-plugin-code-syntax-highlight`](https://github.com/nhn/tui.editor/tree/master/plugins/code-syntax-highlight) | Plugin to highlight code syntax |
| [`@toast-ui/editor-plugin-color-syntax`](https://github.com/nhn/tui.editor/tree/master/plugins/color-syntax) | Plugin to color editing text |
| [`@toast-ui/editor-plugin-table-merged-cell`](https://github.com/nhn/tui.editor/tree/master/plugins/table-merged-cell) | Plugin to merge table columns |
| [`@toast-ui/editor-plugin-uml`](https://github.com/nhn/tui.editor/tree/master/plugins/uml) | Plugin to render UML 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>


## :beginner: Architecture of this project.

![Project Image](project-image-url)

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :zap: Steps to Execute the project. 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :key: Login to AWS Account

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :closed_lock_with_key: Create Key Pairs

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :lock: Create Security groups

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :bulb: Launch Instances with user data 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :earth_africa: Update IP to name mapping in route 53

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :hammer_and_wrench: Build Application from source code

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :rocket: Upload to S3 bucket

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :package: Download artifact to Tomcat Ec2 Instance

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :lock: Setup ELB with HTTPS 

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :earth_africa: Map ELB Endpoint to website name in DNS

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

### :hammer_and_wrench: Build Autoscaling Group for Tomcat Instances

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

## :earth_africa: Verify from browser

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>


## :page_facing_up: Resources

<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>


## :star2: Acknowledgment


<br/>
<div align="right">
    <b><a href="#Project-03">↥ back to top</a></b>
</div>
<br/>

