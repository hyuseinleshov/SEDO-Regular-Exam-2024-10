pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0.x'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'feature-ci-pipeline', url: 'https://github.com/hyuseinleshov/SEDO-Regular-Exam-2024-10.git'
            }
        }

        stage('Setup .NET') {
            steps {
                bat 'dotnet --version'
            }
        }

        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build Application') {
            steps {
                bat 'dotnet build --no-restore --configuration Release'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'dotnet test HouseRentingSystem.UnitTests/HouseRentingSystem.UnitTests.csproj --no-build --configuration Release --verbosity normal'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Tests completed successfully!'
        }
        failure {
            echo '❌ Build or Tests failed!'
        }
    }
}
