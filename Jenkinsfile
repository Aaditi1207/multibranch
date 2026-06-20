pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'main'
                }
            }
            steps {
                echo "Running SonarQube Analysis"
            }
        }

        stage('Upload To Nexus') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'main'
                }
            }
            steps {
                echo "Uploading Artifact To Nexus"
            }
        }

        stage('Deploy To QA Tomcat') {
            when {
                branch 'develop'
            }
            steps {
                echo "Deploying To QA Tomcat"
            }
        }

        stage('Deploy To Production Tomcat') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying To Production Tomcat"
            }
        }
    }
}
