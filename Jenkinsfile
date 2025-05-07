pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Proper Git checkout using SCM step
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: 'main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Abhi-CloudDevops/Terraform_CICD.git'
                    ]]
                ])
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init -input=false'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -out=tfplan'
            }
        }
    }

    post {
        always {
            cleanWs() // Clean workspace post-build
        }
    }
}
