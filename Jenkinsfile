pipeline{
   agent any
   tools{
       maven 'maven'
   }
   stages{
       stage('Build Maven'){
           steps{
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/indrasenareddy1/cicd.git']])
               bat 'mvn clean install'

           }
       }
   }
}
