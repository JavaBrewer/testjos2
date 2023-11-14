pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github_access_token',
                    url: 'https://github.com/JavaBrewer/testjos2.git'
            }
        }
        stage("Build & SonarQube Analysis") {
            agent any
            steps {
                withSonarQubeEnv('SonarQube_server') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
