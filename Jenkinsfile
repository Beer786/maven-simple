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
               
                sh 'mvn clean install'
               
        } 
       
   }
   stage('Archive') {
         steps {
             dir('target') {
               zip zipFile: "snapshot-beer-${env.BUILD_NUMBER}.zip", archive: false, glob: '**/*.jar'
                archiveArtifacts artifacts: "snapshot-beer-${env.BUILD_NUMBER}.zip", fingerprint: true
             }
      } 
      
   }  
    }
}
