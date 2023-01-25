pipeline {
    agent any
    stages {
        stage('Dummy Stage 1')
        {
            steps {
                echo "Some Dummy stage"
            }
        }
        stage('Scan image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'sysdig-secure-api-credentials', passwordVariable: 'SECURE_API_TOKEN', usernameVariable: '')]) {
                    sh '''
                        VERSION=$(curl -L -s https://download.sysdig.com/scanning/sysdig-cli-scanner/latest_version.txt)
                        curl -LO "https://download.sysdig.com/scanning/bin/sysdig-cli-scanner/${VERSION}/linux/amd64/sysdig-cli-scanner"
                        chmod +x ./sysdig-cli-scanner
                        ./sysdig-cli-scanner --apiurl https://us2.app.sysdig.com mongo-express:0.54.0
                    '''
                }
            }
        }
        stage('Scanning Image with Plugin') {
            steps {
                sysdigImageScan engineCredentialsId: 'sysdig-secure-api-credentials', imageName: "quay.io/sysdig/agent-slim:12.8.1"
            }
        }
        stage('Dummy Stage 2')
        {
            steps {
                echo "Some Dummy stage 2"
            }
        }
    }
}