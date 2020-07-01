@Library("SharedLibraries") _

pipeline {
   agent any

    triggers {
        cron('H/10 * * * *')
    }
    options { 
        buildDiscarder(
            logRotator(
                daysToKeepStr: '5',
                numToKeepStr: '15',
                artifactDaysToKeepStr: '5',
                artifactNumToKeepStr:'5'
            )
        ) 
        preserveStashes(buildCount: 5) 
        disableConcurrentBuilds()
    }
   stages {
       stage('Checkout Shared Library') {
           steps {
               script{
                   bootstrap {
                       libraryName   = "isortegah-workflowlibs"
                       libraryBranch = "master"
                       entrypointParams = [
                           nodeLabel         : "bash"
                           
                       ]
                   }
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