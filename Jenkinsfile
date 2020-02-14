pipeline {
    agent any
    stages {
        stage('Create Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params.json --region 'us-east-2'"
              }
             }
            }
            }
