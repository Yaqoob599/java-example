pipeline {
    agent any
    environment {
        SCANNER_HOME= tool 'sonar-scanner'
    }

    stages {
        stage('Checkout Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Yaqoob599/java-example.git'
            }
        }
        
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('SonarQube Analsyis') {
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Java-app -Dsonar.projectKey=Java-app \
                            -Dsonar.java.binaries=. '''
                }
            }
        }
    }
}
