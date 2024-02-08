pipeline {
    agent any

    tools {
        maven "MAVEN3"
        jdk "OracleJDK11"
    }

    stages {
        stage('Fetch Code') {
            steps {
                git branch: 'main', url: 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
            post {
                success {
                    echo 'archiving artifact now'
                    archiveArtifacts '**/*.war'
                }
            }
        }

        stage('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Chekstyle Analysis'){
            steps{
                sh ' mvn checkstyle:checkstyle'
            }
        }
    }
}
