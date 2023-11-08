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
        stage("Build & SonarQube") {
            agent any
            steps {
                withSonarQubeEnv('Sona_TOKEN') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
