pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-west-2', credentials: '	2ff66b3a-f9fc-493f-b3c2-2ece80adf680') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'abdo-bucket-abdo')
        }

      }
    }

  }
}
