pipeline {
    agent any
    stages {
        stage('checkout scm') {
            steps {
                git branch: 'main', url: 'https://github.com/Komalgorde/git-Jenkins'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install flask'
            }
        }

        stage('test') {
            steps {
                sh 'python3 -m py_compile app.py'
            }
        }
        stage('build') {
            steps {
                sh 'python3 app.py &'
                sleep 5
                sh 'curl http://localhost:5000'
            }
        }
    }
}
