def tomcatServerUrl = "http://15.207.108.255:8081/"
pipeline {
  agent any
  tools {
        jdk "jdk17"
    }
  stages {
    //Use this code for inline pipeline script option
     stage('Code checkout') {
      steps {
        //download code from github
        git branch: 'production', credentialsId: 'Git_cred', url: 'https://github.com/Dinesh10275/betav2.git'
      }
    }
    stage ('Build') {
            steps {
                sh 'mvn clean install'
            }
    }
    stage('Deploy') {
      steps {
        //deploy war on tomcat server
       deploy adapters: [tomcat9(credentialsId: '5b630be7-f7e0-4dd1-a4d4-b9d5047ff3e5', path: '', url: 'http://15.207.108.255:8081/')], contextPath: 'demoapp', war: '**/*.war'
      }
    }
  }
}
