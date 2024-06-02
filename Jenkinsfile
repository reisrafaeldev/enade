pipeline {
    agent any

    tools {
        maven "maven_home"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/reisrafaeldev/enade.git']]])
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Scan with SonarQube') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                    sh 'mvn clean verify sonar:sonar \
                          -Dsonar.projectKey=manuten-o \
                          -Dsonar.host.url=http://localhost:9000 \
                          -Dsonar.login=sqp_4f6cbb7e70c9ce441af8461a44888369374e33c9'
                }
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
