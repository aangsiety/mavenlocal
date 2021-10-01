def skipRemainingStages = false
pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
                script {
                    skipRemainingStages = true

                    println "skipRemainingStages = ${skipRemainingStages}"
                }
               
                sh 'mvn compiler'
                
            }
        }
        
        stage ('test maven') {
            when {
                expression {
                    !skipRemainingStages
                }
            }
            steps {
               
                    sh 'mvn test'
                
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
