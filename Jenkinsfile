pipeline {
    agent any
    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }

    stages {
        stage('Fetch code') {
            steps {
                git branch: 'atom', url: 'https://github.com/TiraWeb/vprofile-project.git'
            }
        }

        stage('Unit test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
            post {
                success {
                    echo "Archiving artifact"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

    }

}