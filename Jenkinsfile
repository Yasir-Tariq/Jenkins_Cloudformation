pipeline {
    agent any
    stages {
        stage('Create Cluster Stack') {
          steps {
            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
            sh "aws cloudformation create-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
          }
        }
        // stage('Create Service Stack') {
        //    steps {
        //     sh "aws cloudformation create-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
        //   }
        // }
    }
}
