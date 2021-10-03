def skipRemainingStages = "skip"
pipeline {
    agent any
  

    stages {
        stage ('compile maven') {
            steps {  
            
                    sh 'mvn compile'
               
                
                    script {
                    skipRemainingStages = "notskip"

                    println "skipRemainingStages = ${skipRemainingStages}"
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
