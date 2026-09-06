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
                sh ''' python3 -m venv venv
                ./venv/bin/pip install flask '''
            }
        }

        stage('test') {
            steps {
                sh './venv/bin/python -m py_compile app.py'
            }
        }
        stage('build') {
            steps {
                sh 'nohup ./venv/bin/python app.py > app.log 2>&1 &'
                sleep 5
                sh 'curl http://localhost:5000'
            }
        }
    }
}
