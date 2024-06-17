pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/marcobarem/DevOps-Jenkins.git'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Faz checkout da branch main
                    git branch: 'main', url: "${GIT_REPO}"
                }
            }
        }
        
        stage('Build and Deploy ex1') {
            steps {
                dir('ex1') {
                    script {
                        if (!isCommandAvailable('docker compose')) {
                            error 'docker compose is not available'
                        }
                        sh 'docker compose up -d'
                    }
                }
            }
        }
        
        stage('Build and Deploy ex2') {
            steps {
                dir('ex2') {
                    script {
                        if (!isCommandAvailable('docker compose')) {
                            error 'docker compose is not available'
                        }
                        // Envolva o comando em try-catch para capturar erros de porta
                        try {
                            sh 'docker compose up -d'
                        } catch (Exception e) {
                            echo "Error starting ex2: ${e}"
                            currentBuild.result = 'FAILURE'
                        }
                    }
                }
            }
        }
        
        stage('Build and Deploy ex3') {
            steps {
                dir('ex3') {
                    script {
                        if (!isCommandAvailable('docker compose')) {
                            error 'docker compose is not available'
                        }
                        sh 'docker compose up -d'
                    }
                }
            }
        }
    }

    post {
        always {
            dir('mongo-mongo-express') {
                script {
                    sh 'docker compose down || true'
                }
            }
            dir('mariadb-phpmyadmin') {
                script {
                    sh 'docker compose down || true'
                }
            }
            dir('postgres-dpage/pgadmin4') {
                script {
                    sh 'docker compose down || true'
                }
            }
        }
    }
}

// Função para verificar se um comando está disponível no PATH
def isCommandAvailable(command) {
    return sh(script: "command -v ${command}", returnStatus: true) == 0
}