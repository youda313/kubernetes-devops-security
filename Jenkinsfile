pipeline {
  agent any

  stages {
      stage('Build Artifact - Maven') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }   
    
  
  
      stage('Unit Tests - Maven and Jacoco') {
            steps {
              sh "mvn test"              
            }
        post {
          always {
          junit 'target/surefire-reports/*.xml'
          jacoco execPattern: 'target/jacoco.exec'
          }
        }
        
        } 
    
      stage('Docker build and push') {
        steps {
          sh 'printenv'
          sh 'docker build -t youda313/numeric-app:""$GIT_COMMIT"" .'
          sh 'docker push youda313/numeric-app:""$GIT_COMMIT""'
        }
      }
    
    }
  
}
