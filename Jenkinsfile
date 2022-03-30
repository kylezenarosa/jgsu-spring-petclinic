pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kylezenarosa/jgsu-spring-petclinic.git', branch: 'main'
                
            }
        }
        
        stage('Build') {
            steps {
                  bat 'mvn package'
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}