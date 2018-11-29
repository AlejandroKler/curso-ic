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