node {

  stage ('checkout'){
           git branch: 'main', credentialsId: 'git_creds', url: 'https://github.com/kunchamrajkumar/sample-java-app.git'
 
         }

   stage ('build'){ 
        withMaven(globalMavenSettingsConfig: '', jdk: 'java', maven: 'maven', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn clean package'
           }
   
   }
   stage ('deploy'){
        
           sshagent(['ssh_ID']) {
                  sh "scp -o StrictHostKeyChecking=no webapp/target/*.war ubuntu@44.201.79.229:/usr/local/tomcat9/webapps/ "
                   }
     
   }






}
