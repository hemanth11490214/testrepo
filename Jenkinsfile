pipeline {
 /*  agent any */
     agent {label 'master'}
     stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('checkout') { 
            steps {
               checkout([$class: 'GitSCM', 
               branches: [[name: '*/master']], 
               doGenerateSubmoduleConfigurations: false, 
               extensions: [], 
               submoduleCfg: [], 
               userRemoteConfigs: [[credentialsId: 'ce8e5abb-1452-4578-8d84-0cb0a63fa34a', 
               url: 'https://github.com/hemanth11490214/testrepo.git']]])
            }
        }
        stage('Build') { 
            steps {
                sh "mvn clean install" 
            }
        }
    }
}
