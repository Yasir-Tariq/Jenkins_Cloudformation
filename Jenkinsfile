// pipeline {
//     agent any
//     stages {
//         stage('Create Cluster Stack') {
//           steps {
//             sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
//             sh "aws cloudformation create-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
//             // withAWS(region:'us-east-2'){
//             //   cfnUpdate(stack:'ecs-stack', url:'https://github.com/Yasir-Tariq/Jenkins_Cloudformation/blob/master/ecs.yaml')
//             //   cfnUpdate(stack:'service-stack', url:'https://github.com/Yasir-Tariq/Jenkins_Cloudformation/blob/master/service.yaml')
//             // }
//           }
//         }
//     }
// }
// // sh "aws cloudformation update-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
// // sh "aws cloudformation update-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"



def jenkinsStackUpdateStatus = false
pipeline {
  agent any
     stages {
        stage ('CFN') {
            steps {
                script {
                    if (jenkinsStackUpdateStatus) {
                        stage ('Create Stacks') {
                            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
                            sh "aws cloudformation create-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
                        }
                    }
                    // if (jenkinsStackUpdateStatus = true) {
                    else {    
                        stage ('Modify Stacks') {
                          withAWS(region:'us-east-2') {
                          def output1 = cfnUpdate(stack: "ecs-stack", paramsFile:'params_ecs.json', file:'ecs.yaml')
                          def output2 = cfnUpdate(stack: "service-stack", paramsFile:'params_service.json', file:'service.yaml')

         
                        }
                            // sh "aws cloudformation update-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters file://params_ecs.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
                            // sh "aws cloudformation update-stack --stack-name service-stack --template-body file://service.yaml --parameters file://params_service.json --capabilities CAPABILITY_IAM --region 'us-east-2'"
                        }
                    }
                }
            }
        }
    }
}