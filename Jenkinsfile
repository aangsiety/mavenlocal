def skipRemainingStages = "skip"
pipeline {
    agent any
    parameters {
        booleanParam(name: "RELEASE", defaultValue: false)
    }
  

    stages {
        stage ('compile maven') {
            steps {  
            
                    sh 'mvn compiler'
            }
                
       }
        stage ('test maven') {
            if ( currentBuild.result == "FAILED"){
              when { expression { params.RELEASE } }
            }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
             if ( currentBuild.result == "FAILED"){
              when { expression { params.RELEASE } }
            }
        
            
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
