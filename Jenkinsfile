pipeline {
    agent any

    stages {
        stage('clone data from github') {
            steps {
                echo 'Cloning the Github Data'
                
                git 'https://github.com/navib-007/project-html-website.git'
                
                sh 'ls'
            }
        }
        stage('build docker image and container') {
            steps {
                echo 'Using docker-compose to do the process'
                // calling compose file 
                sh 'docker-compose down'
                sh 'docker-compose up -d --build'
                // checking container
                sh 'docker-compose ps'
                // checking images
                sh 'docker images'
            }
            
        }
        stage('testing container app') {
            steps {
                echo 'testing container health page with curl'
                sh 'curl -f http://localhost:2077/health.html'
            }
            
        }
    }
}
