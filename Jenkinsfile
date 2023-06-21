#!groovy
pipeline {
    //DOCKER_CTR_NAME=mynginx
    agent any
    stages {
	    stage('readfromfile') {                  
     steps {
          script{
                def readpropscontent = readProperties file: 'edgeruntime.properties'
                echo 'readpropscontent ::: '+readpropscontent
                readpropscontent.each{ k,v ->
                    echo "KEY = $k :::: VAL = $v "
                }

             }                         
     }                  
}
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
                bat 'docker stop RAHS_Git_POC_ERT_June0011001'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
		bat 'docker ps'
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                echo "Start Edge Runtime...!!" 
                bat 'docker start RAHS_Git_POC_ERT_June0011001'
            }
        }
    }
}
