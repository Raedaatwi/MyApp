pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', 
                    branches: [[name: '*/master']],
                    extensions: [[$class: 'CloneOption', timeout: 120]],
                        userRemoteConfigs: [[
                            credentialsId: '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', 
                            url: 'https://github.com/Raedaatwi/MyApp.git']]])
                }
            }
        }
       
        }
    
    
