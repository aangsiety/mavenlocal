def skipRemainingStages = "skip"
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn compiler'
                if (currentBuild.result == "FAILED"){
                    script {
                    skipRemainingStages = "notskip"

                    println "skipRemainingStages = ${skipRemainingStages}"
                    }
                    
                }
                 
                   
                }
                
            }
       
        stage ('test maven') {
            when { equals expected: "skip", actual: "${skipRemainingStages}" }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
             when { equals expected: "skip", actual: "${skipRemainingStages}" }
            
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
