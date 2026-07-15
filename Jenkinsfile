pipeline {
    agent any

    stages {

        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m pip install --upgrade pip
                python3 -m pip install -r requirements.txt
                '''
            }
        }

        
        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest'
            }
        }

        stage('Run Application') {
            steps {
                sh 'python3 app.py'
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }
    }
}
