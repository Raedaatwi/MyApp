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
        /*
        stage('Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }
        */
        stage('Build') {
             steps{
                script{
                    sh " ansible-playbook ansible/build.yml -i ansible/inventory/host.yml --private-key=/var/lib/jenkins/.ssh/id_rsa -u root"
                }
            }
        }
        
        stage('Docker'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml --private-key=/var/lib/jenkins/.ssh/id_rsa -u root"
                }
            }
        }
        
        stage('dockerHub') {
             steps{
                script{
                    sh "ansible-playbook ansible/registry.yml -i ansible/inventory/host.yml --private-key=/var/lib/jenkins/.ssh/id_rsa -u root"
                }
            }
        }
        
        }
        }
    
    
