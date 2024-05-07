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
 deploy adapters: [tomcat9(credentialsId: 'ea4dc0af-51e1-4e96-8098-44e40eedffc8', path: '', url: 'http://localhost:8080/')], contextPath: '/ci-cd-jk', war: '**/*.war'
 }
 }
 }
 }
}
