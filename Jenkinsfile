#!groovy
pipeline {
    //DOCKER_CTR_NAME=mynginx
    agent any
    stages {
        stage('Build') { 
            steps {
                //echo "Start Build...!!"
                 bat 'docker --version'
            }
        }
        stage('Test') { 
            steps {
                echo "Start Test...!!"
                bat 'docker stop mynginx'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
            }
        }
        stage('Deploy') { 
            steps {
                echo "Start Deploy...!!" 
                //bat 'docker start mynginx'
            }
        }
    }
}