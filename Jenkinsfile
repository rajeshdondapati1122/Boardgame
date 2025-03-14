pipeline {
    agent any
    

    stages {
        stage('git check') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git_token', url: 'https://github.com/rajeshdondapati1122/Boardgame.git']])
            }
        }
    
        
        
        
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        
        
        stage('docker build') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker_token') {
                        sh 'docker build -t rajeshdondapati309/ekart11:latest .'
                }
               
   
                }
            }
        }
        
        
        stage('docker push') {
            steps {
                script{
                   withDockerRegistry(credentialsId: 'docker_token') {
                        sh 'docker push rajeshdondapati309/ekart11:latest'
                        sh 'docker run -d -p 8070:8080 --name cont1 rajeshdondapati309/ekart11:latest'
                }
               
   
                }
            }
        }
        
        
        
        
    }
}
