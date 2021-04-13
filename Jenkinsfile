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
        stage('Sonar Analisys'){
            environment{
                scannerHome = tool 'SonarScanner'
            }
            steps {f
                withSonarQubeEnv('sonar_local') {
                    sh "${scannerHome}/bin/sonar-scanner
                    -Dsonar.projectKey=DeployBack 
                    -Dsonar.host.url=http://localhost:9000 
                    -Dsonar.login=5ad67fb6ba6acb80219ee51e63f2665b6af0a50 
                    -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**, **/src/test/**,**/model/**,**/Aplication.java"
                }
            }
        }
    }
}

