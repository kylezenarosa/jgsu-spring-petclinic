pipeline {
    agent {
        docker { 
            image 'maven:3.8.4-jdk-11' 
        }
    }
    
    stages {
        stage("Audit Tools") {
            steps {
                sh '''
                    java -version
                    mvn -v
                '''
            }  
        }
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kylezenarosa/jgsu-spring-petclinic.git', branch: 'main'
                
            }
        }
        
        stage('Build') {
            steps {
                  sh 'mvn package'
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