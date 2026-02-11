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

        stage('Build') {
            steps {
                // Using mvn is now possible because of the tools block above
                sh 'mvn clean package'
            }
        } // Missing brace was here
    } // Missing brace for stages was here
} // Missing brace for pipeline was here
