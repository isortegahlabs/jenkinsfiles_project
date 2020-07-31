pipeline {
    agent any
    stages {
        stage('prev'){
            steps {
                sleep 15
            }
        }
    }
    stages {
        agent { 
       docker { image 'maven:slim' } 
        }
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}