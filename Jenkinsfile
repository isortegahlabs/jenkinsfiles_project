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