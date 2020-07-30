pipeline {
   agent { 
       docker { image 'maven:slim' 
       args '-u root -p 8081:8081 -v /var/run/docker.sock:/var/run/docker.sock  '
       } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}