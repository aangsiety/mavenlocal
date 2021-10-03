def skipRemainingStages = false
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn compile'
                    script {
                    skipRemainingStages = true

                    println "skipRemainingStages = ${skipRemainingStages}"
                }
                 
                   
                }
                
            }
       
        stage ('test maven') {
            when { equals expected: false, actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
            
            when { equals expected: false, actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
