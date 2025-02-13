pipeline {
    agent any
    environment {
        name = 'yunus'
    }
    parameters {
            string(name: 'person', defaultValue: 'yunus', description: 'who are you?')
            booleanParam(name: 'ismale', defaultValue: true, description: '')
            choice(name: 'city', choices: ['jaipur','mumbai','pune'], description: '')
    }
    stages {
        stage('run a cmd') {
            steps {
                sh '''
                ls
                pwd
                date
                '''
            }
        }
        stage('environment variable') {
            steps {
                echo "${BUILD_ID}"
                echo "${name}"
                sh 'echo "${APP}"'
            }
        }
        stage('Build') {
            steps {
                withEnv(['APP=COC']) {
                    echo "${BUILD_ID}"
                    echo "${name}"
                    sh 'echo "${APP}"'
                }
            }
        }

        stage('parameters') {
            steps {
                sh 'echo "${person}"'
                sh 'echo "${ismale}"'
                sh 'echo "${city}"'
            }
        }
        stage('continue ?') {
            input {
                message "should we continue?"
                ok "yes we should"
            }
            steps {
                echo 'asking for continue'
            }
        }
        stage('Deploy on prod') {
            steps {
                echo 'deploy on prod'
            }
        }
    }
    post {
        always {
            echo "This will always run, no matter what."
        }
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed! Check logs."
        }
    }
}
