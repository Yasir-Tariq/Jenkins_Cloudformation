pipeline {
  agent any
     stages {
        stage ('CFN') {
            steps {
                script {
                  withAWS(region:'us-east-2') {
                          def ecs_stack = cfnUpdate(stack: "ecs-stack", paramsFile:'params_ecs.json', file:'ecs.yaml')
                          def service_stack = cfnUpdate(stack: "service-stack", paramsFile:'params_service.json', file:'service.yaml')
                        }
                }
            }
        }
    }
}