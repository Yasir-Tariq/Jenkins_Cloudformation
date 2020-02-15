pipeline {
    agent any
    stages {
        stage('Create Cluster Stack') {
          steps {
            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
            sh "aws cloudformation create-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
            withAWS(region:'us-east-2'){
              def output1 = cfnUpdate(stack:'ecs-stack', url:'https://github.com/Yasir-Tariq/Jenkins_Cloudformation/blob/master/ecs.yaml')
              def output2 = cfnUpdate(stack:'service-stack', url:'https://github.com/Yasir-Tariq/Jenkins_Cloudformation/blob/master/service.yaml')
            }
          }
        }
    }
}
