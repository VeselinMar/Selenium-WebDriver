pipeline {
    agent any

    stages {
        stage('Checkout the repository') {
            steps {
                checkout scm
            }
        }

        stage('Restore the project') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build the project') {
            steps {
                sh 'dotnet --version'
                sh 'dotnet build'
            }
        }

        stage('Run tests') {
            parallel {
                stage('TestProject1 UI tests') {
                    steps {
                        sh 'dotnet test TestProject1 --no-build --verbosity normal'
                    }
                }
                stage('TestProject2 UI tests') {
                    steps {
                        sh 'dotnet test TestProject2 --no-build --verbosity normal'
                    }
                }
                stage('TestProject3 UI tests') {
                    steps {
                        sh 'dotnet test TestProject3 --no-build --verbosity normal'
                    }
                }
            }
        }

    }

    post {
        always {
            echo 'Pipeline Completed'
        }
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}