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
                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=manutencao -Dsonar.host.url=http://localhost:9000 -Dsonar.login=squ_a642e2bcd679bd5a7118e6330ba81a6da8b2bf92'
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
