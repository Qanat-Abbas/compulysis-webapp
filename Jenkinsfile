pipeline {
    agent any

    environment {
        EMAIL = "qanatabbas14@gmail.com"
    }
    stages {
        stage('Build') {
            steps {
                sh 'rm -rf compulysis-webapp'
                sh 'git clone https://github.com/Qanat-Abbas/compulysis-webapp'
                dir('compulysis-webapp') {
                    sh 'docker compose down --remove-orphans'
                    sh 'docker compose up -d'
                }
            }
        }
    }

    post {
        success {
            emailext (
                subject: "SUCCESS: ${env.JOB_NAME}",
                body: "Build Successful ✅",
                to: "${EMAIL}"
            )
        }

        failure {
            emailext (
                subject: "FAILED: ${env.JOB_NAME}",
                body: "Build Failed ❌",
                to: "${EMAIL}"
            )
        }
    }
}
