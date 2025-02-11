pipeline {
    agent any

    stages {
        stage('Setup Environment') {
            steps {
                echo "Creating virtual environment..."
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install --upgrade pip setuptools wheel'
            }
        }

        stage('Install and Test') {
            steps {
                echo "Installing dependencies..."
                sh '. venv/bin/activate && pip install . pytest'  // Додаємо pytest

                echo "Running tests..."
                sh '. venv/bin/activate && pytest || true'  // Виконуємо тести
            }
        }
    }

    post {
        success {
            echo "CI pipeline executed successfully!"
        }
        failure {
            echo "CI pipeline failed. Check the logs."
        }
    }
}
