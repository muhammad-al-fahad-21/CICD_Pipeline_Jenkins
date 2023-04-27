pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                npm install
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                npm run test
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                curl -X POST -H "Content-Type: application/json" -d '{\"username\":\"myuser\", \"password\":\"mypassword\"}' https://mydeploymentlink.com/deploy
                '''
            }
        }
    }
}
