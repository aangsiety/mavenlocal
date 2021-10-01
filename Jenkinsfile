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
            when {
                expression {
                    !skipRemainingStages
                }
            }
            steps {
               
                    sh 'mvn tes'
                
            }
        }
      
        stage ('build maven') {
            when {
                expression {
                    !skipRemainingStages
                }
            }
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
