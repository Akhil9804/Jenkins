pipeline {
    agent{
        docker{
            image "amazon/aws-cli:latest"
            args "--entrypoint=''"
        }        
    }

    stages {
        stage('Build') {
            environment{
                AWS_DEFAULT_REGION='ap-south-1'
            }

            steps {
                withCredentials([usernamePassword(credentialsId: 'AWS-ACCESS-KEY', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh 'aws s3 ls'
                }
            }
        }
    }
}
