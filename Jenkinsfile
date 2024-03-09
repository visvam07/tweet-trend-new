pipeline {
    agent {label 'maven'}

    environment {
        PATH = "/apache-maven-3.9.6/bin:$PATH"
    }

    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}