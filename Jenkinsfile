pipeline {
    agent any
    stages {
        stage('Build-backend'){
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests'){
            steps {
                sh 'mvn test'
            }
        }
     stage ('Sonar Analysis') {
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                    sh "${scannerHome}/bin/sonar-scanner -e 
                    -Dsonar.projectKey=DeployBack 
                    -Dsonar.host.url=http://localhost:9000 
                    -Dsonar.login=cf6826d57f1e453e08ecbd6cf862496472061f66 
                    -Dsonar.java.binaries=target 
                    -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java"
                }
            }
        }
    }
}

