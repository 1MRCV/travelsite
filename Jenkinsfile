pipeline {
    agent { label 'windows-agent' }

    environment {
        DEPLOY_DIR = "C:\\inetpub\\wwwroot\\travelsite"
    }

    stages {

        stage('Prepare Deployment Directory') {
            steps {
                bat '''
                if exist "%DEPLOY_DIR%" (
                    rmdir /S /Q "%DEPLOY_DIR%"
                )
                mkdir "%DEPLOY_DIR%"
                '''
            }
        }

        stage('Deploy to IIS') {
            steps {
                bat '''
                xcopy /Y /E /I "%WORKSPACE%\\*" "%DEPLOY_DIR%\\"
                '''
            }
        }
    }

    post {
        success {
            echo "Travelsite deployed successfully to IIS!"
        }
        failure {
            echo "Deployment failed. Please check logs."
        }
    }
}
