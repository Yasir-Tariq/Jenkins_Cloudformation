pipeline {
    agent any
    stages {
        stage('Create Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name ec2 --template-body file://ecs.yaml --region 'us-east-2'"
            sh "echo 'Created...'"
              }
             }
            }
            }
