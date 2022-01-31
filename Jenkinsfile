pipeline {
    agent {label "test-label"}

    tools {
        maven "maven-3.6.3"
    }
    stages {
        stage('Build') {
            steps {
                git branch: 'dev', url: 'https://github.com/devopsdsvc/core-app.git'
                sh "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean deploy"
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
