pipeline {
  agent any

  stages {
      stage('Build Artifact - Maven') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }   
    }
  
  stages {
      stage('Unit Tests - Maven') {
            steps {
              sh "mvn test"
              
            }
        }   
    }
  
}
