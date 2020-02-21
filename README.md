# Jenkins_automated_Cloudformation
Provisioning AWS ECS resources thorugh Cloudformation templates and Jenkins automation.


## Pre Reqs

Following pre requisites are necessary for proper understanding:
- AWS services knowledge
- Groovy syntax for Jenkins Pipelines

## Plugins

Following plugins are required for this project:
- pipeline: AWS Steps
- git


## Files
This repository consists only one file, the cloudformation templates for provisioning ECS resources are stored in s3 bucket:

1.Jenkinsfile: contains Jenkins Pipeline code.


## Explanation

In this project, we are using the "Declarative" approach for building the Jenkins pipeline.
Therefore, Source Code Management (SCM) is used to get this repository to be fed to the
Jenkins Pipeline. Also, we will be using Git Webhooks to notify Jenkins about the latest push
event so that the build automatically triggers itself whenever any git change occurs.
You can add a webhook in the repository settings and the URL would be the Jenkins URL followed
by the port 8080.
e.g, http://some-url:8080/github-webhook/

Now, form the pipeline AWS Steps plugin we are using the cfnUpdate() function which will take 
the Cloudformation templates from the s3 bucket specified and it will create or update the
resources. If there is no resources, then it will create them or if any changes are required,
then it will update them accordingly. The pipeline is parametrized for getting neccesary values
from the user's end



