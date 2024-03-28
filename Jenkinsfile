pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
  bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '96f1b69f-3e45-4f65-8cf8-d4dfcea7c9d5', path: '', url: 'http://localhost:8080/')], contextPath: 'calculator', war: '**/*.war'
 }
 }
 }
 }
}

