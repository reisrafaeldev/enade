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
            withSonarQubeEnv(installationName: 'manutencao') {
                sh """
                mvn clean verify sonar:sonar \
                -Dsonar.projectKey=manutencao \
                -Dsonar.host.url=http://sonarqube:9000 \
                -Dsonar.login=sqp_b1bffd137768e79c7c38bc550d90f822f7b64838
            """
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
