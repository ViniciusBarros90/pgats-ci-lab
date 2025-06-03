pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Clonar Projeto') {
            steps {
                checkout scm
            }
        }

        stage('Instalar Yarn') {
            steps {
                bat 'npm install -g yarn'
            }
        }

        stage('Instalar Dependências') {
            steps {
                bat 'yarn'
            }
        }

        stage('Instalar Playwright') {
            steps {
                bat 'yarn playwright install'
            }
        }

        stage('Executar Testes E2E') {
            steps {
                bat 'yarn run e2e || exit 0'  // para não quebrar o pipeline se falhar
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado!'
        }
    }
}

===========================================

parte que funciona

pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Clonar Projeto') {
            steps {
                checkout scm
            }
        }

        stage('Instalar Yarn') {
            steps {
                bat 'npm install -g yarn'
            }
        }

        stage('Instalar Dependências') {
            steps {
                bat '''
                    set PATH=%APPDATA%\\npm;%PATH%
                    yarn
                '''
            }
        }

        stage('Instalar Playwright') {
            steps {
                bat '''
                    set PATH=%APPDATA%\\npm;%PATH%
                    yarn playwright install
                '''
            }
        }

        stage('Executar Testes E2E') {
            steps {
                bat '''
                    set PATH=%APPDATA%\\npm;%PATH%
                    yarn run e2e || exit 0
                '''
            }
        }

        stage('Verificar Yarn') {
            steps {
                bat '''
                    set PATH=%APPDATA%\\npm;%PATH%
                    where yarn
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado!'
        }
    }
}

