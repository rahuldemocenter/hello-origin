#!groovy
pipeline {
    //DOCKER_CTR_NAME=mynginx
    agent any
    stages {
        stage('Start') { 
            steps {
                //echo "Start step...!!"
                 bat 'docker --version'
				 bat 'docker ps'
            }
        }
        stage('Stop Edge Runtime') { 
            steps {
                echo "Start Test...!!"
                bat 'docker stop myEdgeServerRAHS03'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
			   bat 'docker ps'
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                echo "Start Deploy...!!" 
                bat 'docker start myEdgeServerRAHS03'
				echo "Trying to start Edge Runtime instance....!!"
				bat 'docker ps'
            }
        }
    }
}