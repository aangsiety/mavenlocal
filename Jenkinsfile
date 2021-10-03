def skipRemainingStages = 1
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn compile'
                    script {
                    skipRemainingStages = 2

                    println "skipRemainingStages = ${skipRemainingStages}"
                }
                 
                   
                }
                
            }
       
        stage ('test maven') {
            when { equals expected: 2, actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
            
            when { equals expected: 2, actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
