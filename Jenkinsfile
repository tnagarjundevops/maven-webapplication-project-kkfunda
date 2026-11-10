//scripted way PL for web application

node
{

   // /var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven-3.9.6/bin

   def mavenHome = tool name: "maven-3.9.6"

   stage('git checkout')
   {
      git branch: 'master', url: 'https://github.com/tnagarjundevops/maven-webapplication-project-kkfunda.git'
   }
   stage('compile')
   {
     sh "${mavenHome}/bin/mvn compile"
   }
   stage('Build')
   {
     sh "${mavenHome}/bin/mvn clean package"
   }
   stage('Sonar')
   {
     sh "${mavenHome}/bin/mvn sonar:sonar"
   }
    stage('Nexus')
   {
     sh "${mavenHome}/bin/mvn deploy"
   }

  stage('Deploy to Tomcat')
  {
      sh """

      curl -u nagarjun:Durvik@232023 \
--upload-file /var/lib/jenkins/workspace/webapp-scripted-way-pipe/target/maven-web-application.war \
"http://13.127.55.140:8080/manager/text/deploy?path=/maven-web-application&update=true"
          
        """
  }


} //node ending
