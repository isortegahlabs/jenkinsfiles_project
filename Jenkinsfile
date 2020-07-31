pipeline {
    agent any

    stages {
        stage('verify'){
            steps {
                sleep 1
            }
        }
        stage('build') {
            agent { 
                docker { image 'maven:slim' } 
            }
            steps {
                sh 'mvn --version'
            }
        }
    }
}