pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                   echo "Multiline shell steps works too"
                   ls -lah
                '''   
            }
        }
        stage ('Upload to AWS'){
            steps {
                withAWS(region: 'us-west-2', credentials: 'AKIAWSKQJ3WIYEO7YC7V') {
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'project3bucket')
                }
            }
        }
    }
}
