pipeline {
    agent any

    stages {
        stage('Build') {

            agent{
                docker{
                    image "amazon/aws-cli:latest"
                    args "--entrypoint=''"
                }        
            }

            environment{
                AWS_DEFAULT_REGION='us-east-1'
            }

            steps {
                withCredentials([usernamePassword(credentialsId: 'AWS-ACCESS-KEY', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh '''
                        aws s3api create-bucket \
                        --bucket aws-bucket-0535 \
                        --region $AWS_DEFAULT_REGION
                        aws s3 ls
                    '''
                }
            }
        }
    }
}
