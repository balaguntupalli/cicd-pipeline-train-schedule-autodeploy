# cicd-pipeline-train-schedule-autodeploy from applicatgion build from jenkins and push to AWS ECR and deploy into AWS EKS.

This is a simple train schedule app written using nodejs. It is intended to be used as a sample application for a series of hands-on learning activities.

## Running the app

You need a Java JDK 7 or later to run the build. You can run the build like this:

    ./gradlew build

You can run the app with:

    ./gradlew npm_start

Once it is running, you can access it in a browser at http://localhost:8080

##  Note: In this setup we are usinng AWS cli credentails to provide ECR and EKS access to Jenkins

### jenkins setup command
```
apt-get install openjdk-8-jdk -y  
vi /etc/profile
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/
export PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
save and exit
source /etc/profile
### gradle setup 


### install Jenkins plugins
1.Amazon ECR plugin
2.Kubernetes Continuous Deploy Plugin

after that authenticating ECR and EKS access work start
----
### creating 
dfdf
