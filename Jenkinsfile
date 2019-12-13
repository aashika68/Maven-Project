pipeline {
   
   agent any 
   tools {
    maven 'Apache Maven 3.6.2'
  }
 
    stages {
       
       stage('Checkout'){
          steps{
          sh 'rm -rf Maven-Project'
          sh 'git clone https://github.com/VivekRaveendrn/Maven-Project.git'
          }
       }
       
       
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
       
       stage('Sonarqube') {
   
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
       
       
      
    }
}
