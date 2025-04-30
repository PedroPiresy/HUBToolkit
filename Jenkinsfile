pipeline {
    agent {
        docker {
            image 'debian:12'  // Usando a imagem oficial do Debian 12
            args '-u root'  // Permite a execução de comandos como root
        }
    }

    triggers {
        githubPush() // Dispara o build quando houver push no GitHub
    }

    environment {
        REPO_URL = 'https://github.com/SamSepi0l13/HUBToolkit.git'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                // Atualiza o repositório e instala curl e git no Debian 12
                sh '''
                    apt-get update
                    apt-get install -y curl git
                '''
            }
        }

        stage('Clone Repository') {
            steps {
                // Clona o repositório HUBToolkit
                sh '''
                    git clone ${REPO_URL}
                '''
            }
        }

        stage('Run Scripts') {
            steps {
                // Executa os scripts do repositório (modifique conforme necessário)
                sh '''
                    cd HUBToolkit
                    chmod +x *.sh
                    ./some_script.sh  # Substitua por um script válido dentro do repositório
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline Finalizado!'
        }
    }
}
// teste