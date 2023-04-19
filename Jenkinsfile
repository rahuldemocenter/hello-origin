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
                bat 'docker stop RAHS_Edge_Runtime04'
               echo "Trying to stop running instance"
               //docker stop $DOCKER_CTR_NAME > /dev/null 2>&1; echo $
		bat 'docker ps'
            }
        }
        stage('Start Edge Runtime') { 
            steps {
                //echo "Start Deploy...!!" 
                //bat 'docker start RAHS_Edge_Runtime04'
		//echo "Trying to start Edge Runtime instance....!!"
		    def response = httpRequest "https://originawsdev1.dev-int-aws-us.webmethods.io/integration/rest/origin/agent/generatecode/"
		    println('Status: '+response.status)
		    println('Response: '+response.content)
		echo "Start New Edge Runtime.....................................!!" 
                bat 'docker run -p 5555:5555 -d -e SAG_IS_CLOUD_REGISTER_URL=https://originawsdev1.dev-int-aws-us.webmethods.io -e SAG_IS_EDGE_TENANT_ID=originawsdev1 -e SAG_IS_EDGE_CLOUD_ALIAS=EdgeServer_RAHS_Edge_Runtime06 -e SAG_IS_CLOUD_REGISTER_TOKEN=2f840873f0d740a38dac4021f5cef7f4f7673d3242304c309fc9ef9c1ce99b16 --name=RAHS_Edge_Runtime06 iregistry.eur.ad.sag/origin/webmethods-edge-runtime:latest'
		echo "Trying to start new instance"
		bat 'docker ps'
            }
        }
    }
}
