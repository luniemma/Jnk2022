pipeline {
    agent any
    stages {
        stage('Download') {
           steps {
              git branch: 'ops', url: 'https://github.com/luniemma/JENKINS_REPO.git'
           }
        } 
         stage   ('Build') {
           steps{
                 sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                  deploy adapters: [tomcat8(credentialsId: 'dev', path: '', url: 'http://10.0.28.141:8080')], contextPath: 'qaenv', war: '**/*.war'
                }
            }
        }
   }
