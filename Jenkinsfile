pipeline {
   agent none   
    stages {
        stage('Verify') {
            agent{ label 'bash2'}
            steps {
                echo "Hello World"
                sleep 5
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                script {
                    //sh "env"
                    //echo sh(returnStdout: true, script: 'env|sort')
                    //sh 'printenv'
                    /*
                    def envs = sh(returnStdout: true, script: 'env').split('\n')
                    envs.each { e ->
                        it = e.split("=")
                        println "Name: ${it[0]} Value ${it[1]}"
                    }*/

                    printParams()

                }
            }   
        }
        stage('Validate') {
            steps {
                echo "Stage Validate"
                sleep 2
            }
        }
        stage('Compile') {
            agent{ label 'bash'}
            tools {
                maven 'mvn'
            }
            steps {
                sh 'mvn compile'
            }
        }
        stage('testUT') {
            agent{ label 'bash'}
            steps {
                withMaven(maven: 'mvn') {
                    sh 'mvn test'
                }
            }
        }
        stage('Build') {
            agent{ label 'bash'}
            steps {
                echo "Stage Build"
                sleep 2
            }
        }
        stage('parallel tests'){
            parallel {
                stage('testAT') {
                    agent{ label 'bash'}
                    steps {
                        echo "Stage testAT"
                        sleep 2
                    }
                }
                stage('testIT') {
                    agent{ label 'bash2'}
                    steps {
                        echo "Stage testIT"
                        sleep 2
                    }
                }
            }
        }
        stage('parallel deploy'){
            parallel {
                stage('Deploy') {
                    agent{ label 'bash'}
                    steps {
                        echo "Stage Deploy"
                        sleep 2
                    }
                }
                stage('Docker') {
                    agent{ label 'bash2'}
                    steps {
                        echo "Stage Docker"
                        sleep 2
                    }
                }
            }
        }
        stage('Release') {
            agent{ label 'bash'}
            steps {
                echo "Stage Release"
                sleep 2
            }
        }
    }
   post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}

@NonCPS
def printParams() {
    env.getEnvironment().each {
        name , value -> println "Name: $name Value -> $value"
    }
}