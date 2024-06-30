pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Restore dependencies and build
                    sh "dotnet restore"
                    sh "dotnet build --configuration Release"
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests
                    sh "dotnet test --configuration Release --logger trx"
                }
                junit 'Tests/**/*.trx'
            }
        }
        stage('Publish') {
            steps {
                script {
                    // Publish artifacts or deploy
                    sh "dotnet publish --configuration Release --output publish"
                }
                archiveArtifacts 'publish/**'
            }
        }
    }
}
