pipeline {
    agent any

    stages {
        stage('code fetch from github') {
            steps {
               echo 'cloning the github code for the next process'
               git branch: 'branch1', url: 'https://github.com/TechWithKhanam/simple-java-maven-app.git'
            }
        }
        
        stage('building code using mvn') {
            steps {
               echo 'Maven triggered, build going on'
               sh 'mvn clean install'
            }
        }
            
        stage('test code using Surefire') {
            steps {
               echo 'testing code'
               sh 'mvn test'
            }
        }
        
        stage('verify Dockerfile') {
            steps {
                echo 'Verifying Dockerfile presence'
                sh 'dir'
            }
        }
        
        stage('build Docker image') {
            steps {
                echo 'build Docker image'
                 sh 'docker build -t myapp1:latest .'
            }
        }
        
        stage('Deployment using docker') {
            steps {
                echo 'deploying'
                 sh 'docker run -d -p 9090:8080 --name myapp_container myapp1:latest'
            }
        }
    }
 }
