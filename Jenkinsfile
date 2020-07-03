pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Run') {
            steps {
                sh '''
                   mvn jar:jar install:install help:evaluate -Dexpression=project.name
                   java -jar target/websocket-demo-0.0.11-SNAPSHOT.jar
            }
        }
    }
}
