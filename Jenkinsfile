pipeline {
    agent any
    stages {
        stage('Create Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
              }
             }
            }
            }
