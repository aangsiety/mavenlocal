pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn compile'
                
            }
        }
        
        stage ('test maven') {
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
