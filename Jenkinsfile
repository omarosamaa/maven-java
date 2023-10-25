pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages {
        stage('build jar') {
            steps {
                echo 'building the jar'
                sh 'mvn package'
            }
        }
        stage('making the image and pushing to docker') {
            steps {
                echo 'building the jar'
                sh 'docker build -t omar64/nana_project:2.3 .'
                withCredentials([usernamePassword(credentialsId: 'DockerHub', usernameVariable: 'user', passwordVariable: 'pass')]) {
                    sh 'docker login -u user -p pass'
                }
                sh 'docker push omar64/nana_project:2.3'
            }
        }        
        stage('deployment') {
            steps {
                echo 'deploying'
            }
        }
        
    }
}
