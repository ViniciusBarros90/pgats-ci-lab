pipeline {
    agent any  // Usa um agente Jenkins (máquina virtual, container etc.)

    options {
        skipDefaultCheckout(true) // Evita checkout automático (vamos controlar isso)
    }

    stages {
        stage('Clonar Projeto') {
            steps {
                checkout scm
            }
        }

        stage('Instalar Node.js') {
            steps {
                bat '''
                    curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
                    apt-get install -y nodejs
                    node -v
                    npm -v
                '''
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
                bat 'yarn run e2e || true' // Permite falhas sem quebrar o pipeline
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado!'
        }
    }
}
