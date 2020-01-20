pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now archiving....'
                    archiveArtifacts artifacts: '**/targert/*.war'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}
