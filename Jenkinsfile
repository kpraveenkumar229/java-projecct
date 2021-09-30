pipeline{
    agent any
    stages{
        stage('Checkout-Stage'){
            steps{
                 git 'https://github.com/kpraveenkumar229/java-projecct.git'
            }
        }
        stage('Build-Stage'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Execute-SonarQube-Report'){
            steps{
                sh 'mvn sonar:sonar'
            }
        }
        stage('Uploda-artifact-into-Nexus'){
            steps{
                sh 'mvn deploy'
            }
        }
        stage('Deploy-into-Tomcat'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'b7c76d91-1a89-4b3c-b418-8234a9ccdaed', path: '', url: 'http://15.206.164.223:8080/')], contextPath: null, onFailure: false, war: '**/maven-web-application.war'
            }
        }
    }
 }

