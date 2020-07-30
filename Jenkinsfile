pipeline {
   agent { 
       docker { image 'maven:slim' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}