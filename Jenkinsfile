pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/DatZeroSize/Devopslab2.git'
            }
        }
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                bat 'dotnet build --configuration Release'
            }
        }
        stage('Publish') {
            steps {
                bat 'dotnet publish -c Release -o ./publish'
            }
        }
    }
}
