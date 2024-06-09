pipeline {
    agent any

    tools {
        maven "MAVEN"

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

    stage('SonarQube Analysis') {
        steps {
            withSonarQubeEnv('manutencao') {
                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=manutencao'
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
