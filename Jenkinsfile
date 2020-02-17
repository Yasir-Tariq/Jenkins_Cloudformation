pipeline {
  agent any
  parameters {
        string(name: 'stackecs', defaultValue: 'ecs-stack22', description: 'Enter the stack name for ecs cluster')
        string(name: 'stackservice', defaultValue: 'service-stack', description: 'Enter the stack name for ecs service')
        string(name: 'ecsAMI', defaultValue: 'ami-035ad8e6117e5fde5', description: 'Enter AMI for ECS.')
        string(name: 'KeyName', defaultValue: 'yasirKP-ohio', description: 'Enter key pair name.')
        string(name: 'ClusterName', defaultValue: 'mycluster', description: 'Enter AMI for ECS.')
        string(name: 'InstanceType', defaultValue: 't2.small', description: 'Enter type for ECS instance.')
        string(name: 'DBfromSSM', defaultValue: 'MYSQL_ROOT_PASSWORD', description: 'DB password value from AWS Systems manager.')
        string(name: 'TargetGroupName', defaultValue: 'mytg', description: 'Enter Target group name.')
        string(name: 'WebECRImage', defaultValue: '020046395185.dkr.ecr.us-east-2.amazonaws.com/newphpimage:latest', description: 'Enter ECR Repo for web app.')
        string(name: 'MysqlECRImage', defaultValue: '020046395185.dkr.ecr.us-east-2.amazonaws.com/mysql:5.6', description: 'Enter ECR repo for mysql.')
        string(name: 'ALBName', defaultValue: 'myalb', description: 'Enter name for the Application Load Balancer.')
        string(name: 'HealthPath', defaultValue: '/', description: 'Enter path for health checks.')
           }
     stages {
        stage ('CFN') {
            steps {
                script {
                  withAWS(region:'us-east-2') {
                          def ecs_stack = cfnUpdate(stack: "${params.stackecs}", params:['ecsAMI':"${params.ecsAMI}",'KeyName':"${params.KeyName}",'ClusterName':"${params.ClusterName}",'InstanceType':"${params.InstanceType}"], url:'https://for-nested-stacks.s3.us-east-2.amazonaws.com/ecs.yaml')
                          def service_stack = cfnUpdate(stack: "${params.stackservice}", params:['DBfromSSM':"${params.DBfromSSM}",'ClusterName':"${params.ClusterName}",'TargetGroupName':"${params.TargetGroupName}",'WebECRImage':"${params.WebECRImage}",'MysqlECRImage':"${params.MysqlECRImage}",'ALBName':"${params.ALBName}",'HealthPath':"${params.HealthPath}"] , url:'https://for-nested-stacks.s3.us-east-2.amazonaws.com/service.yaml')
                        }
                }
            }
        }
    }
}


