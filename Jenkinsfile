pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    triggers {
  pollSCM '* * * * *'
}





    stages {
       
        stage('build') {
            steps {
                echo 'Hello Build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        
         stage('test') {
            steps {
                sh 'mvn test'
                
            }
        }
        
        stage ('build and publish image') {
      steps {
        script { 
          checkout scm
          docker.withRegistry('', ' DockerUserID') {   
          def customImage = docker.build("bertinlekane/holly-pipeline:${env.BUILD_ID}")
          def customImage1 = docker.build("bertinlekane/holly-pipeline")
          customImage.push()
          customImage1.push()
          }
    }

  
    } 

}         
     
 } 
    
}

