pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 echo 'Building...'
                 // sh "exit 1"
             }
             post {
                 always {
                     jiraSendBuildInfo site: 'planetaryrobotics.atlassian.net'
                 }
             }
         }
         stage('Deploy - Staging') {
             steps {
                 echo 'Deploying to Staging from master...'
             }
             post {
                 always {
                     jiraSendDeploymentInfo site: 'planetaryrobotics.atlassian.net', environmentId: 'us-stg-1', environmentName: 'us-stg-1', environmentType: 'staging'
                 }
             }
         }
         stage('Deploy - Production') {
            steps {
                echo 'Deploying to Production from master...'
            }
            post {
                always {
                    jiraSendDeploymentInfo site: 'planetaryrobotics.atlassian.net', environmentId: 'us-prod-1', environmentName: 'us-prod-1', environmentType: 'production'
                }
            }
         }
     }
 }