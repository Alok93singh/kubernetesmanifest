jenkins files for argocd


We need to send BUILD_NUMBER variable to fetch latest image tag in deployment pipeline.

Here are we sending using DOCKERTAG Varibale name in our update manifesh job.

##Steps to trigger updatemanifest job:


 
pipeline {  
    agent any
    stages{
      stage("test manifest"){
          steps{
          echo "triggering updatemanifestjob"
          build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: "199")]
          }
      }
    }
}
