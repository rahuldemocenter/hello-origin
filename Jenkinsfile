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
		echo "Start New Edge Runtime.....................................!!" 
                bat 'docker run -p 5555:5555 -d -e SAG_IS_CLOUD_REGISTER_URL=https://originawsdev1.dev-int-aws-us.webmethods.io -e SAG_IS_EDGE_TENANT_ID=originawsdev1 -e SAG_IS_EDGE_CLOUD_ALIAS=EdgeServer_RAHS_ABCD01 -e SAG_IS_CLOUD_REGISTER_TOKEN=12cc1d85fe8a47f6a2d8a46ed6ee6d4367960a5422194803b39de979162bf6a4 --name=RAHS_ABCD01 iregistry.eur.ad.sag/origin/webmethods-edge-runtime:latest'
		echo "Trying to start new instance"
		bat 'docker ps'
            }
        }
    }
}
