pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                
            }
        } 
        stage('build') {
            steps {
                echo 'Hello Build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        
         stage('deploy') {
            steps {
                echo 'Hello Deploy'
                
            }
        }
        
        
       stage('test') {
            steps {
                echo 'Hello Test'
                
            }
        }  
        
    }
}

