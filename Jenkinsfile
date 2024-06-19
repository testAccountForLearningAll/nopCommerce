pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('scm') {
            steps {
                git url: 'https://github.com/rajithaYadav-15/nopCommerce.git',
                    branch: 'develop'
            }
        }
        stage('build') {
            steps {
            	mail bcc: '', body: 'Build Started', cc: '', from: '', replyTo: '', subject: 'Build Started', to: 'jenkinsamplesmtp@gmail.com'
                //sh 'dotnet publish -o published/ -c Release src/Presentation/Nop.Web/Nop.Web.csproj'
                dotnetPublish configuration: 'Release',
                    outputDirectory: 'published',
                    project: 'src/Presentation/Nop.Web/Nop.Web.csproj'
                mail bcc: '', body: 'Build completed', cc: '', from: '', replyTo: '', subject: 'Build completed', to: 'jenkinsamplesmtp@gmail.com'

            }
            post {
                success {
                    zip zipFile: 'nop.web.zip',
                      archive: true,
                      dir: './published',
                      overwrite: true
                }
            }
        }

    }
}