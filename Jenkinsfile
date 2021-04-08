node
{

  //def mavenHome=tool name: "maven3.6.3"
  
 stage('Checkout')
 {
 git credentialsId: 'git', url: 'https://github.com/narendrankn/maven_web_app.git'
 }
 
 stage('Build')
 {
 sh  "${M2_HOME}/bin/mvn clean package"
 }
 
 stage('ExecuteSoanrQubeReport')
 {
   sh  "${M2_HOME}/bin/mvn sonar:sonar"
 }
 
 stage('UploadArtifactintoNexus')
 {
 sh  "${M2_HOME}/bin/mvn deploy"
 }
 
 stage('DeployAppintoTomcat')
 {
sshagent(['tomcat1']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ubuntu@13.127.251.198:/opt/tomcat/webapps"
 }
 }
 
}
