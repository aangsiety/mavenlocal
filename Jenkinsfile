pipeline {
    agent any
  

    stages {
        stage ('compile maven') {
            steps {  
            
                    sh 'mvn compile'
               
                
                    script {
                        env.TRIGGER_NEXT = true
                   
                    }
                 }
                
            }
        stage ('test maven') {
            when { 
                expression {
                    env.TRIGGER_NEXT == true
                }
            }
            steps {
               
                    sh 'mvn test'
                
            }
        }
      
        stage ('build maven') {
             when { 
                expression {
                    env.TRIGGER_NEXT == true
                }
            }
         
            
            steps {
               
                    sh 'mvn package'
                
            }
        }
    }
}
