pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }

    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }   
    
    stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                scp -v -i /path/to/your/private-key.pem -o StrictHostKeyChecking=no target/dptweb-1.0.war ec2-user@34.201.103.128:/prod/apache-tomcat-8.5.96/webapps/webap.war

              }      
           }       
    }
    
  }
}
