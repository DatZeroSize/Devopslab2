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
                bat 'dotnet publish -c Release -o D:\\C#\\Devops\\publish'
            }
        }

        stage('Deploy to IIS') {
            steps {
                // Dừng website trên IIS trước khi copy file
                bat 'iisreset /stop'

                // Copy files sang thư mục IIS (wwwroot)
                bat 'robocopy D:\\C#\\Devops\\publish C:\\inetpub\\wwwroot\\DevopsApp /E /PURGE'

                // Khởi động lại IIS
                bat 'iisreset /start'
            }
        }
    }
}
