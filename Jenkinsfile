pipeline {
    agent any
    tools { 
        maven 'maven-3.6.1' 
        jdk 'jdk8' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

       stage('Build') {
           steps {    
               dir('maven-pipeline') {
                sh 'mvn clean install'
               }
        } 
       
   }
   stage('Archive') {
         steps {
             dir('maven-pipeline/target') {
           archive '*.jar'
             }
      } 
      
   }  
    }
}
