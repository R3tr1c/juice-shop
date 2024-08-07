pipeline {
    agent any

    environment {
        PATH = "${HOME}/.local/bin:${PATH}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install semgrep') {
            steps {
                // Устанавливаем semgrep
                script {
                    // Пакетный менеджер pip должен быть установлен на вашем агенте
                    sh 'pip install semgrep'
                }
            }
        }

        stage('Run semgrep') {
            steps {
                // Запускаем semgrep
                script {
                    sh "semgrep scan ."
                }
            }
        }
    }

    post {
        always {
            // Дополнительно: можете добавить шаги для обработки результатов, например, уведомления или архивации артефактов
            echo 'Pipeline finished'
        }
    }
}
