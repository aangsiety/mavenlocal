def skipRemainingStages = "skip"
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
                try {
                    sh 'mvn compile'
                }
                catch (e) {
                    script {
                    skipRemainingStages = "notskip"

                    println "skipRemainingStages = ${skipRemainingStages}"
                    }
                    throw e
                 
                }
                    
                
                
                   
                }
                
            }
       
        stage ('test maven') {
            when { equals expected: "notskip", actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
             when { equals expected: "notskip", actual: "${skipRemainingStages}" }
            
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
