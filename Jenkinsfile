pipeline {
    agent any

    stages {
        stage ('compile maven') {
            steps {
               
                    sh 'mvn compilerr'
                    script {
                       skipRemainingStages = true
                       try {
                            println("In if block")
                            skipRemainingStages = true
                          }
                       catch (Exception exc) {
                              println("Exception block: ${exc}")
                              skipRemainingStages = false
                          }

                        if (skipRemainingStages) {
                             currentBuild.result = 'FAILURE'
                              error("Stopping early!")
                        }
                          }
                   
                }
                
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
