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
                echo "Stop Edge Runtime...!!"
                bat 'docker stop RAHS_Edge_Runtime_Ubuntu'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
		bat 'docker ps'
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                echo "Start Edge Runtime...!!" 
                bat 'docker start RAHS_Edge_Runtime04'
            }
        }
    }
}
