pipeline {
    agent any

    stages {
        stage('Source') {
            steps {
                git 'https://github.com/emilioflc/UNIR.EntornosCICD.Actividad3.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building stage!'
                sh 'make build'
            }
        }

        stage('Unit tests') {
            steps {
                echo 'Running unit tests...'
                sh 'make test-unit'
                archiveArtifacts artifacts: 'results/*.xml', fingerprint: true
            }
        }

        stage('API tests') {
            steps {
                echo 'Running API tests...'
                sh 'make test-api'
                archiveArtifacts artifacts: 'results/*.xml', fingerprint: true
            }
        }

        stage('E2E tests') {
            steps {
                echo 'Running E2E tests...'
                sh 'make test-e2e'
                archiveArtifacts artifacts: 'results/*.xml', fingerprint: true
            }
        }
    }

    post {
        failure {
            /*
            mail to: 'dev-team@example.com',
                 subject: "Fallo en el job ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: """El pipeline del job ${env.JOB_NAME} ha fallado en la ejecución #${env.BUILD_NUMBER}.
Se han ejecutado todas las fases (unit, API, E2E) y al menos una ha fallado.
Revisa los informes de pruebas adjuntos en Jenkins."""
            */

            echo "SIMULACIÓN EMAIL -> El job ${env.JOB_NAME} ha fallado en la build #${env.BUILD_NUMBER}"
        }
    }
}
