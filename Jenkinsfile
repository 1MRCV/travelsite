pipeline {
    agent { label 'windows-agent' }

    environment {
        DEPLOY_DIR = "C:\\inetpub\\wwwroot\\travelsite"
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/1MRCV/travelsite.git', branch: 'master'
            }
        }

        stage('Deploy to IIS') {
            steps {
                bat '''
                if not exist "%DEPLOY_DIR%" (
                    mkdir "%DEPLOY_DIR%"
                )
                xcopy /Y /E /I "%WORKSPACE%\\*" "%DEPLOY_DIR%\\"
                '''
            }
        }
    }
}
