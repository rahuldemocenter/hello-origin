#!groovy
def ERT_LIST = []
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
				ERT_LIST = readpropscontentfile2.tokenize(":");
				echo 'ERT_LIST ::: '+ERT_LIST
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
		     script {
		    for (int i = 0; i < ERT_LIST.size(); i++) {
               		 bat 'docker stop ERT_LIST[i]'
              		 echo "Trying to stop running instance ERT_LIST[i]"
		    }
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
		bat 'docker ps'
		     }
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                echo "Start Edge Runtime...!!" 
                bat 'docker start $readpropscontentfile2'
            }
        }
    }
}
