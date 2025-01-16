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
        stage ('sonar analysis'){
            steps{
                sh 'mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=cicd-deploy \
                      -Dsonar.host.url=http://15.206.94.130:9000 \
                      -Dsonar.login=squ_52adeabc24df0c7bff0d7faa18d3bbd2527f5c66'
            }
        }
    }
}
