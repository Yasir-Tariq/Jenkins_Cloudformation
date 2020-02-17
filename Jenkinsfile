pipeline {
  agent any
  parameters {
        string(name: 'ecs', defaultValue: 'ecs-stack', description: 'enter the stack name for ecs cluster')
        string(name: 'service', defaultValue: 'service-stack', description: 'enter the stack name for ecs service')
           }
     stages {
        stage ('CFN') {
            steps {
                script {
                  withAWS(region:'us-east-2') {
                          def ecs_stack = cfnUpdate(stack: "${params.ecs}", paramsFile:'params_ecs.json', file:'ecs.yaml')
                          def service_stack = cfnUpdate(stack: "${params.service}", paramsFile:'params_service.json', file:'service.yaml')
                        }
                }
            }
        }
    }
}




