pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/DatZeroSize/Devopslab2.git'
            }
        }

        stage('Stop IIS') {
            steps {
                bat 'iisreset /stop' 
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
                bat 'dotnet publish -c Release -o D:\\C#\\Devops\\publish'
            }
        }

        stage('Deploy to IIS') {
            steps {
          
                bat 'xcopy /E /Y D:\\C#\\Devops\\publish\\* D:\\C#\\Devops\\'

            
                bat 'iisreset /start'
            }
        }
    }
}
