pipeline {
    agent any
    environment {
        //be sure to replace "sampriyadarshi" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "063369903090.dkr.ecr.ap-southeast-1.amazonaws.com/enseval-demo"
        CANARY_REPLICAS = 0
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $DOCKER_IMAGE_NAME:$BUILD_NUMBER ."
                }
            }
        }
        stage('Push Docker Image') {
            docker.withRegistry('https://063369903090.dkr.ecr.ap-southeast-1.amazonaws.com', 'ecr:ap-southeast-1:ecr-cred') {
                sh "docker push 063369903090.dkr.ecr.ap-southeast-1.amazonaws.com/enseval-demo:$BUILD_NUMBER"
            }
        }
        
        stage('DeployToProduction') {
            steps {
                milestone(1)
                kubernetesDeploy(
                    kubeconfigId: 'kubeconfig',
                    configs: 'train-schedule-kube.yml',
                    enableConfigSubstitution: true
                )
            }
        }
    }
    /*post {
	always {
            kubernetesDeploy (
                kubeconfigId: 'kubeconfig',
                configs: 'train-schedule-kube-canary.yml',
                enableConfigSubstitution: true
            )
        }
	*/    
        //cleanup {
	    
	    /* Use slackNotifier.groovy from shared library and provide current build result as parameter */   
        //    slackNotifier(currentBuild.currentResult)
            // cleanWs()
        //}
   // }
}
