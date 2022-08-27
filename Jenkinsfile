pipeline {
    agent any
    tools {
        maven "maven:3.5.0"
    }
    stages {
        stage('Version') {
            steps {
                sh "mvn --version"
            }
        }
        stage('Install') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t grupo03/spring-petclinic:latest .'
            }
        }
        stage('SonarQube') {
            steps{
                withSonarQubeEnv('spring-petclinic') { 
                    sh "mvn sonar:sonar"
                }
            }
        }
        stage('JUnitTest'){
            steps{
                sh "mvn clean compile test"
            }
        }
    }
}
