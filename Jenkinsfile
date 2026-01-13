pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/nigirimeshi02/JenkinsTest'
            }
        }

        stage('Build') {
            steps {
                bat '''
                "C:\Program Files\Microsoft Visual Studio\2022\Community\Msbuild\Current\Bin\MSBuild.exe" ^
                GitTest\\GitTest.sln ^
                /p:Configuration=Release ^
                /p:Platform=x64
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/Release/*.exe', fingerprint: true
        }
        failure {
            echo 'Build Failed'
        }
    }
}
