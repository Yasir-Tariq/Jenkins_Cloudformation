pipeline {
    agent any
    stages {
        stage('Create Stack') {
            steps {
            sh "aws cloudformation create-stack --stack-name ecs-stack --template-body file://ecs.yaml --parameters ecsAMI=ami-035ad8e6117e5fde5,KeyName=yasirKP-ohio,ClusterName=myCluster,InstanceType=t2.small --region 'us-east-2'"
            sh "echo 'Created...'"
              }
             }
            }
            }
