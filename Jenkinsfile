pipeline {
    agent any 
    
    tools {
        // Ensure 'Maven' matches the name configured in 'Global Tool Configuration'
        maven 'Maven'
    }
    
    stages {
        stage('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
       stage('Git secret checks') {
         steps {
           sh 'rm tufflehog || true'
           sh 'docker run gesellix/trufflehog --json https://github.com/kanr20478-hub/webapp.git > trufflehog'
           sh 'cat trufflehog'
         }
       }
        stage('Build') {
            steps {
                // Using mvn is now possible because of the tools block above
                sh 'mvn clean package'
            }

         } // Missing brace was here
            stage ('Deploy-To-Tomcat') {
            steps {
           
            sh  'scp  target/*.war /scratch/tomcat/apache-tomcat-10.1.52/webapps/webapp.war'
              }      
           }       
    
    } // Missing brace for stages was here
} // Missing brace for pipeline was here
