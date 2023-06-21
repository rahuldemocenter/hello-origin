#!groovy
pipeline {
    //DOCKER_CTR_NAME=mynginx
    agent any
    stages {
	    stage('readfromfile') { 
		steps {
		      script{
		            def readpropscontent = readFile file: 'edgeruntime.properties'
		            echo 'readpropscontent ::: '+readpropscontent
		            
		            for (String item : readpropscontent.split('\n')) {
		                echo "item ::: "+item
		                def readpropscontentfile2 = item.split("=")[1];
		                echo 'readpropscontentfile2 ::: '+readpropscontentfile2
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
                bat 'docker stop readpropscontentfile2'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
		bat 'docker ps'
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                echo "Start Edge Runtime...!!" 
                bat 'docker start readpropscontentfile2'
            }
        }
    }
}
