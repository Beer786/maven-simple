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
 // stage('Archive') {
  //       steps {
    //         dir('target') {
    //             zip zipFile: "snapshot-${env.JOB_NAME}-${env.BUILD_NUMBER}.zip", archive: false, glob: '**/**'
    //            archiveArtifacts artifacts: "snapshot-${env.JOB_NAME}-${env.BUILD_NUMBER}.zip", fingerprint: true
    //         }
    //  } 
      
//}
 stage('Archive') {
         steps {
             archiveArtifacts 'target/*zip'
      } 
       }  

    }
}
