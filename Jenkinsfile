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
                bat 'dotnet publish -c Release -o D:\\C#\\Devops\\bin\\Release\\net8.0\\publish'
            }
        }

        stage('Deploy to IIS') {
            steps {
                // Copy files sang thư mục IIS
                bat 'xcopy /E /Y D:\\C#\\Devops\\bin\\Release\\net8.0\\publish\\* D:\\C#\\Devops\\'

                // Restart IIS để nhận code mới
                bat 'iisreset'
            }
        }
    }
}
