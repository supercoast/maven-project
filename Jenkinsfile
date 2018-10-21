pipeline {
    agent any

    parameters {
        string(name: 'tomcat-dev', defaultValue: '', description: 'Staging server')
        string(name: 'tomcat-prod', defaultVaule: '', description: 'Production server')
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }

        }
    }
}