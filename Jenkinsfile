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
        stage("test") {
            step{
                echo "---------------unit test started-------------"
                sh 'mvn surefire-report:report'
                echo "--------------unit test completed------------"
            }
        }
        stage("sonarQube analysis") {
            environment {
                scannerHome = tool 'sonar-scanner'
            }

            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}