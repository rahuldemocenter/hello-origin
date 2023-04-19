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
		   script {
                    //I want to get the same response here
                    def response = sh(script: 'curl https://originawsdev1.dev-int-aws-us.webmethods.io/integration/rest/origin/agent/generatecode?name:RAHS_Test_My_ERT&description=  \
  -H "Accept: application/json, text/plain, */*" \
  -H "Accept-Language: en,fr;q=0.9,en-US;q=0.8,es;q=0.7,uk;q=0.6" \
  -H "Connection: keep-alive" \
  -H "Content-Type: application/json" \
  -H "Origin: https://originawsdev1.dev-int-aws-us.webmethods.io" \
  -H "Referer: https://originawsdev1.dev-int-aws-us.webmethods.io/" \
  -H "Sec-Fetch-Dest: empty" \
  -H "Sec-Fetch-Mode: cors" \
  -H "Sec-Fetch-Site: same-origin" \
  -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36" \
  -H "authtoken: flc0019814bfa8c1772b2e77" \
  -H "environment;" \
  -H "sec-ch-ua: "Chromium";v="112", "Google Chrome";v="112", "Not:A-Brand";v="99"" \
  -H "sec-ch-ua-mobile: ?0" \
  -H "sec-ch-ua-platform: "Windows"" \
  -H "x-csrf-token: d0d24654-3428-465c-bb07-ee8132d72b0e" \
 // --data-raw '{"name":"RAHS_Test_My_ERT","description":""}' \
  --compressed', returnStdout: true)
                    echo '=========================Response===================' + response
                }
		echo "Start New Edge Runtime.....................................!!" 
                bat 'docker run -p 5555:5555 -d -e SAG_IS_CLOUD_REGISTER_URL=https://originawsdev1.dev-int-aws-us.webmethods.io -e SAG_IS_EDGE_TENANT_ID=originawsdev1 -e SAG_IS_EDGE_CLOUD_ALIAS=EdgeServer_RAHS_Edge_Runtime06 -e SAG_IS_CLOUD_REGISTER_TOKEN=2f840873f0d740a38dac4021f5cef7f4f7673d3242304c309fc9ef9c1ce99b16 --name=RAHS_Edge_Runtime06 iregistry.eur.ad.sag/origin/webmethods-edge-runtime:latest'
		echo "Trying to start new instance"
		bat 'docker ps'
            }
        }
    }
}
