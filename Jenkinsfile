pipeline {
    agent any
    tools {
        nodejs "v18.20.3"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/reisrafaeldev/test-jenkins.git']]])
            }
        }

/*         stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm run test'
            }
        }

        stage('Scan with SonarQube') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                    sh 'sonar-scanner -Dsonar.projectKey=my-react-app -Dsonar.sources=src -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqp_5af1336f1d35228322371a9fe7000234eb91fcf6'
                }
            } */
        }
    }
}