pipeline {
    agent any
    triggers { 
        pollSCM('* * * * *')
    }
    stages {
        stage('scm') {
            steps {
                git url: 'https://github.com/testAccountForLearningAll/nopCommerce.git', branch: 'develop'
            }
        }
        stage('build) {
            steps {
                sh 'dotnet publish -o published/ -c Release src/Presentation/Nop.Web/Nop.Web.csproj'
            }
        }
    }
}