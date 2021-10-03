pipeline {
    agent any
  

    stages {
        stage ('compile maven') {
            steps {  
            
                    sh 'mvn compilerr'
               
                
                    script {
                        env.TRIGGER_NEXT = "true"
                   
                    }
                 }
                
            }
        stage ('test maven') {
            when { 
                expression {
                    environment name: "TRIGGER_NEXT", value: "true"
                }
            }
            steps {
               
                    sh 'mvn test'
                    script {
                        env.TRIGGER_NEXT = "true"
                
            }
        }
      
        stage ('build maven') {
           when { 
                expression {
                    environment name: "TRIGGER_NEXT", value: "true"
                }
            }
            
            steps {
               
                    sh 'mvn package'
                    script {
                        env.TRIGGER_NEXT = "true"
                
            }
        }
    }
}
