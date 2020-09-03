pipeline {
    agent any
    triggers {
  pollSCM '* * * * *'
}




    tools {
        maven 'M2_HOME'
    }
      
    
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
          docker.withRegistry('', ' DockerRegistryID') {   
          def customImage = docker.build("bertinlekane/holly-pipeline:${env.BUILD_ID}")
          def customImage1 = docker.build("bertinlekane/holly-pipeline")
          customImage.push()
          customImage1.push()
          }
    }

  
    } 

}         
      stage ('deployment trigger' ){
          steps {
              build 'holly-CD'
 }                
 }             
                              
  }

    


