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
        stage('delete') {
            agent any
            steps {
                sh 'docker rmi $(docker images |egrep maven| cut -c43-54)'
            }
        }
    }
}