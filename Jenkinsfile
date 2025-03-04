pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Клонирование репозитория с GitHub
                git url: 'https://github.com/scorpelord/sdvps-materials.git', branch: 'main'
            }
        }

        stage('Test') {
            steps {
                // Запуск тестов Go
                sh 'go test .'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Сборка Docker-образа
                sh 'docker build -t scorpelord/sdvps-materials .'
            }
        }
    }

    post {
        always {
            // Всегда выводить логи после завершения
            echo 'Pipeline завершен.'
        }
        success {
            echo 'Pipeline успешно завершен.'
        }
        failure {
            echo 'Pipeline завершился с ошибкой.'
        }
    }
}
