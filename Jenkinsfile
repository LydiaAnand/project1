pipeline{

   agent any

   // agent { label ‘jenkins2’ }

  //  tools{
                  // MAVEN "M3"
 //       }
   stages{
            stage('checkout')
            {
              steps
              {
                  echo "sum checkout"
				     git 'https://github.com/LydiaAnand/project1.git'
              }
            }
        
    stage('Build'){
                    steps{
                              echo "Build"
							  sh 'mvn package'
                         }
                  }
    stage('artifact upload'){
                               steps{
                                       echo "nexus"
									    nexusArtifactUploader artifacts: [[artifactId: 'project1', classifier: '', file: '/root/.jenkins/workspace/testjob_1/target/project1.war', type: 'war']], credentialsId: '9881ca06-0e32-4514-85d3-3de87d356d80', groupId: 'google', nexusUrl: '192.168.4.23:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.0-SNAPSHOT'
                                    }
                            }
    stage('deploy'){
                     steps{
                             echo "Deploy to webserver"
							  sh 'cp /root/.jenkins/workspace/testjob_1/target/project1.war /root/software/tomcat/apache-tomcat-9.0.79/webapps/'
                          }
                   }
    }

}
