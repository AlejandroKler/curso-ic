pipeline {
    agent any
    triggers {
        pollSCM('H/2 * * * *')
    }
    stages {
        stage('Build') {
         steps {
             println 'aca va el build'
             sh './build.sh'
         }
         post{
            always{
                println "ava se exportan los resultados de los test unitarios"
                junit 'build/test-results/test/*.xml'
            }
         }

        }
        stage('Deploy') {
          steps {
              println 'aca va el deploy'
              sh './deploy.sh'
          }
        }
        stage('Verify') {
           steps {
               println 'aca va el verify'
               sh './verify.sh'
           }
           post{
               always{
                   println "ava se exportan los resultados de los test de aceptación"
                   junit 'build/test-results/verify/*.xml'
               }
           }
        }

    }
    post {
        success {
            echo 'El job finalizó OK! :)'
        }
        failure {
            echo 'El job rompio! :('
        }
    }
}