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
                    def response = bat(script: 'curl https://originawsdev1.dev-int-aws-us.webmethods.io/integration/rest/origin/agent/generatecode/ \
  -H "Accept: application/json, text/plain, */*" \
  -H "Accept-Language: en,fr;q=0.9,en-US;q=0.8,es;q=0.7,uk;q=0.6" \
  -H "Connection: keep-alive" \
  -H "Content-Type: application/json" \
  -H "Cookie: lang=en; apt.uid=AP-BCBBKBNAYWW6-2-2-1679290908335-14677246.0.2.1f906cf3-12ca-40aa-9b8c-cc50c52f96a7; route=1681897604.843.190.181298|58fb03e5a1678771a75dea209604055b; login=; SameSite=Lax; userId=-2; apt.sid=AP-BCBBKBNAYWW6-2-2-1681905004199-32186235; OAuth_Token_Request_State=22a58a67-61e3-4d32-b14c-460d0670b800; JSESSIONID=93084E279B06E2ECC5F6564A9E2C1F82" \
  -H "Origin: https://originawsdev1.dev-int-aws-us.webmethods.io" \
  -H "Referer: https://originawsdev1.dev-int-aws-us.webmethods.io/" \
  -H "Sec-Fetch-Dest: empty" \
  -H "Sec-Fetch-Mode: cors" \
  -H "Sec-Fetch-Site: same-origin" \
  -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36" \
  -H "authtoken: fl14acbdd3f229855482cbd2" \
  -H "environment;" \
  -H "sec-ch-ua: "Chromium";v="112", "Google Chrome";v="112", "Not:A-Brand";v="99"" \
  -H "sec-ch-ua-mobile: ?0" \
  -H "sec-ch-ua-platform: "Windows"" \
  -H "x-csrf-token: 8f1039ab-8959-4527-b5b5-d8585d8dd0f8" \
				       ', returnStdout: true)
                    echo '=========================Response===================' + response
                }
		echo "Start New Edge Runtime.....................................!!" 
                bat 'docker run -p 5555:5555 -d -e SAG_IS_CLOUD_REGISTER_URL=https://originawsdev1.dev-int-aws-us.webmethods.io -e SAG_IS_EDGE_TENANT_ID=originawsdev1 -e SAG_IS_EDGE_CLOUD_ALIAS=RAHS_Test_My_ERT01 -e SAG_IS_CLOUD_REGISTER_TOKEN=12cc1d85fe8a47f6a2d8a46ed6ee6d4367960a5422194803b39de979162bf6a4 --name=RAHS_Test_My_ERT01 iregistry.eur.ad.sag/origin/webmethods-edge-runtime:latest'
		echo "Trying to start new instance"
		bat 'docker ps'
            }
        }
    }
}
