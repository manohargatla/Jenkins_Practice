# Jenkins
* Jenkins is an open source continuous integration/continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.
# Story of Jenkins
![preview](images/jnks1.png)
# Need for Continuous Integration
* Traditional Software Project Lifecycle
![preview](images/jnks2.png)
* Big Bang Integrations, were used by teams traditionally to combine components as each component was built by teams in isolation.
![preview](images/jnks3.png)
* Result of BigBang
![preview](images/jnks4.png)
# Continuous Integration (CI): 
* Continuous integration (CI) is the practice of `automating the integration of code changes from multiple contributors into a single software project.` It's a primary DevOps best practice, allowing developers to frequently merge code changes into a central repository where builds and tests then run.
* In this we integrate all the components of the application from day 1. Ideally whenver developer pushes the code to remote repository we need to perform integration.
* To check whether CI is successful or not a small set of automated tests were developed i.e.
  * We build all the application components
  * Integrate them and run this small set of tests which checks basic functionality of the system (Smoke Tests)
* Developers have started writing unit tests (test code which tests the application code)
* To measure the accuracy of unit tests generally we need a tool which measures coverage i.e. code coverage
* Code Coverage: Generally these are measure by tools
  * Line Coverage: Line coverage is a basic version of test coverage. When a test suite is run, code coverage records which lines of code were hit. Line coverage, thus, is the total number of lines run divided by the number of lines in the codebase.
  * branch coverage: how many of the branches of the control structures (if statements for instance) have been executed. 
  * symbol Coverage: The Business Auto Policy uses numeric symbols to indicate the types of vehicles for which coverage is in effect. Only those symbols listed for a coverage can be used. Symbols 1 through 6 provide vehicle automatic coverage. Symbol 1 includes Hired and Non-Owned auto coverage.
* To verify the quality of code and whether it suits your organization’s coding standards, Code Reviews are conducted.
* For coding standards and best practices we can use tools. The failures represented by these tools are generally referred as
  * Technical debt: he implied cost incurred when businesses do not fix problems that will affect them in the future. Accruing technical debt causes existing problems to get worse over time. The longer debt builds up, the more costly it becomes to rectify.
  * Code Smell: A maintainability issue that makes your code confusing and difficult to maintain.
* The tool for running tests is called as test harness tool or popularly know as __test runners__. For running unit tests
  * junit (java)
  * pytest (python)
  * jasmine (nodejs)
  * nunit (c-sharp)
* To check code coverage and code qualilty we have a tool which are generally referred as Static Code Analysis Tools. We will be using __Sonar Qube__ We need a tool which whenever a code is pushed to vcs, builds the code, runs the unit tests and also generates __Static Code Analysis__ report. These tools are referred as CI/CD Engines. 
* Some of the popular CI/CD Engines are
  * Jenkins
  * Azure DevOps Pipelines
  * Travis CI
  * Team City
  * Bamboo
# Build and Artifact
* Build represents a format/package into which your application code is transformed to run on enduser systems.
* To Generate Package we need to perform certain steps
    * compile
    * package
# Building Java
* To make it simple to build java code , Apache foundation has created a tool called as Ant
* In __Ant__ we configure the build using build.xml Refer Here
* Then a tool called as Maven was released which can perform
    * build
    * packaging
    * dependency management
    * documenation
* Maven goes with Convention over Configuration and all of them are around a file which is referred as pom.xml (project object model)
* Maven has a lifecycle
    * validate
    * compile
    * test
    * package
    * install
    * deploy
    * clean
* Every CI/CD Engine is Cron on steriods
# Dependencies
* All the development projects depend on external libraries
    * Java: maven packages
    * node js: npm packages
    * python: pip packages
    * dotnet: nuget packages
* There is a need for managing dependencies
# Installing Maven
* **Maven:** Maven is a popular open-source build tool developed by the Apache Group to build, publish, and deploy several projects at once for better project management. The tool provides allows developers to build and document the lifecycle framework.
* Maven helps developers manage Java-based apps through projects that organize and handle code files & build scripts to execute and run compiler tools, version no. for compiled code, plus dependency management that allows one project to reference a version of other projects.
* To install Maven java to be installed
# Setting Environmental Variables 
* Install java and Check the java by run below commands
```
sudo apt update
sudo apt install openjdk-11-java -y
java -version
whereis java
```
![preview](images/jnks5.png)
![preview](images/jnks6.png)
![preview](images/jnks8.png)
![preview](images/jnks7.png)
* Changing environmental variable from jdk-17 to jdk-11
![preview](images/jnks9.png)
* Maven install
```
sudo apt update
sudo apt install maven -y
mvn --version
```
![preview](images/jnks10.png)
![preview](images/jnks11.png)
* Maven will download all the necessary dependencies to compile/package/test from a maven central repository url@https://mvnrepository.com/repos/central and it downloads to M2_HOME which is by default `<HOME-DIR>/.m2` which is referred as local repository.
    * Maven Lifecycle Phases
    * compile: Will create .class files
    ![preview](images/jnks13.png)
    * test: will run unit tests
    * package: will create package (jar/war)
    * install: will copy the project which you have build to the local repository. Along with jar/war files a pom also gets copied.
    ![preview](images/jnks12.png)
    * clean: It will remove all the packages 
    ![preview](images/jnks14.png)
    ![preview](images/jnks15.png)
# game-of-life 
* GitHub url@https://github.com/wakaleo/game-of-life.git clone the url into your machine
* build the maven package `mvn package and mvn install`
![preview](images/jnks13.png)
![preview](images/jnks14.png)
* To run the application `mvn jetty:run`
![preview](images/jnks16.png)
![preview](images/jnks17.png)
# Jenkins installation
* Jenkins is an open source CI/CD Engine.
* Jenkins:
* Using Package managers on Linux
    Docker
    Windows
    WAR
* Lets install Jenkins Refer Here url@https://www.jenkins.io/doc/book/installing/linux/
* Lets install LTS (Long Term Support Version)
```
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```
![preview](images/jnks18.png)
![preview](images/jnks19.png)
* To access the jenkins `http://<ip_adddress>:8080`
![preview](images/jnks20.png)
* Click on install suggested plugins
![preview](images/jnks21.png)
![preview](images/jnks22.png)
![preview](images/jnks23.png)
# First Project to display some system information
* Lets create a Jenkins project which displays
* username
* current working directory
* java version
* all the environmental variables
* Lets start by create a Jenkins project (Freestyle)
![preview](images/jnks24.png)
![preview](images/jnks25.png)
![preview](images/jnks26.png)
![preview](images/jnks27.png)
![preview](images/jnks28.png)
![preview](images/jnks29.png)
# Node configuration
* Select Manage jenkins => Creadentials => Add global
![preview](images/jnks35.png)
* Select Manage jenkins => Nodes & clouds => New agent
![preview](images/jnks32.png)
![preview](images/jnks33.png)
![preview](images/jnks34.png)
![preview](images/jnks36.png)
![preview](images/jnks37.png)
# Free Style projects
# Game-of-life
* Lets Create a Free style project of Game-of-life Project
![preview](images/jnks39.png)
![preview](images/jnks40.png)
* Lets do global tool configuration for Maven & Java
![preview](images/jnks41.png)
![preview](images/jnks42.png)
* Create a freestyle with below steps
![preview](images/jnks43.png)
![preview](images/jnks44.png)
![preview](images/jnks45.png)
![preview](images/jnks46.png)
![preview](images/jnks47.png)
# Maevn Project for JFROG
* Create a JFROG free Trial account from below steps
![preview](images/jnks48.png)
![preview](images/jnks49.png)
![preview](images/jnks50.png)
* After successfull creation of account Create a user, Group and Access Token
![preview](images/jnks51.png) 
![preview](images/jnks52.png)
![preview](images/jnks53.png) 
# Setting up JFROG in Jenkins 
* Open jenkins server and Install the required plugin for jfrog
* To install plugins Go to Manage jenkins -> Plugins -> click on available plugins and Search for **Artifactory Plugin** and Install
![preview](images/jnks54.png)
* Adding Jfrog Credentials to the jenkins Manage jenkins -> Credentials -> select kind as a secret text
![preview](images/jnks55.png)
* Configure the JFROG to jenkins from Manage jenkins -> System -> select for JFROG Fill the required details and test the connection from there it self by selecting 'Test connection'
![preview](images/jnks56.png)
* After configuration, Create a Repository in JFROG cloud 
* Click on create repo and select required package 'MAVEN' and create
![preview](images/jnks57.png)
![preview](images/jnks58.png)
* Now Create a Free style MAVEN project for spring petclinic by following
![preview](images/jnks59.png)
![preview](images/jnks66.png)
![preview](images/jnks67.png)
![preview](images/jnks68.png)
![preview](images/jnks69.png)
![preview](images/jnks70.png)
* Write a Declarative pipeline to publish artifacts to JFROG cloud 
```Jenkinsfile
pipeline {
    agent { label 'Jenkins_one' }
    triggers { pollSCM ('* * * * *') }
    tools {
        jdk 'JDK_17'
        maven 'MAVEN_HOME'
    }
    stages {
        stage('source code') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage('Artifactory configuration') {
            steps {
                rtServer (
                    id: "MY_JFROG_CLOUD",
                    url: 'https://qtdevopps.jfrog.io/artifactory',
                    credentialsId: 'JFROG_ACCESS'
                )
                rtMavenDeployer (
                    id: "SPC_DEPLOYER",
                    serverId: "MY_JFROG_CLOUD",
                    releaseRepo: 'manu-app-libs-release',
                    snapshotRepo: 'manu-app-libs-snapshot'
                )
            }
        }
        stage('build package') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_HOME',
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "SPC_DEPLOYER"
                )
                rtPublishBuildInfo (
                    serverId: "MY_JFROG_CLOUD"
                )
            }
        }
    }
}
```
![preview](images/jnks71.png)
![preview](images/jnks72.png)
# SonarQube scanner for Static Code Analysis
* Create a SonarQube/Cloud account with gmail or github account
* Create an organization and project for static code analysis
![preview](images/jnks61.png)
* To configure the sonar cloud to jenkins Generate a token in sonar cloud from below steps
![preview](images/jnks62.png)
* Download the **SonarQube Scanner** plugin from manage jenkins => Plugins => available plugins.
![preview](images/jnks63.png)
* After that add credentials to jenkins server and configure the Sonar cloud in manage jenkins => system
![preview](images/jnks64.png)
![preview](images/jnks65.png)
* Write a pipeline steps for static code analysis 
```
pipeline {
    agent { label 'Jenkins_one' }
    triggers { pollSCM ('* * * * *') }
    tools {
        jdk 'JDK_17'
        maven 'MAVEN_HOME'
    }
    stages {
        stage('source code') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage('Artifactory configuration') {
            steps {
                rtServer (
                    id: "MY_JFROG_CLOUD",
                    url: 'https://qtdevopps.jfrog.io/artifactory',
                    credentialsId: 'JFROG_ACCESS'
                )
                rtMavenDeployer (
                    id: "SPC_DEPLOYER",
                    serverId: "MY_JFROG_CLOUD",
                    releaseRepo: 'manu-app-libs-release',
                    snapshotRepo: 'manu-app-libs-snapshot'
                )
            }
        }
        stage('build package') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_HOME',
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "SPC_DEPLOYER"
                )
                rtPublishBuildInfo (
                    serverId: "MY_JFROG_CLOUD"
                )
            }
        }
        stage('static code analysis') {
            steps {
                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh 'mvn clean package sonar:sonar -Dsonar.organization=spring-app \
                        -Dsonar.token=632633c374ac9c0b5c164dd9c1b79aa623cd0b6f \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.projectKey=spring-app_springpetclinic'
                }
            }
        }
    }
}
```
* Build the project
![preview](images/jnks73.png)
![preview](images/jnks74.png)



