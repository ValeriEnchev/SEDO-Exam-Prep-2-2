pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // Optional: polling trigger (use Webhooks instead if possible)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                echo 'Restoring dependencies...'
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the solution...'
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
