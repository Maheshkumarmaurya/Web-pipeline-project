pipeline {
    agent {
        label 'slave2'
    }
    stages {
        stage ('checkout') {
       steps{
           git 'https://github.com/ReyazShaik/java-project-maven-new.git'
          }  
       }
      stage ('compile'){
          steps{
                sh 'mvn compile'
          }
         }
         stage ('Test'){
             steps{
                 sh 'mvn test'
             }
         }
         stage ('Artifacts'){
             steps{
                 sh 'mvn clean package'
             }
         }
         stage ('Deploy'){
             steps{
               deploy adapters: [tomcat9(credentialsId: 'Tomcatcredentials', path: '', url: 'http://15.207.117.115:8080/')], contextPath: 'mywebapp', onFailure: false, war: '**/*.war'
             }
         }
    }
}