pipeline {
    agent any
  
    parameters {
        choice(
            choices: 'proj1\nproj2',
            description: '',
            name: 'REQUESTED_ACTION'
            )
        string(defaultValue: 'master', description: '', name: 'gitBranch')
        booleanParam(defaultValue: true, description: '', name: 'userFlag1')
       
      
        
    }

    
    environment { 
            
                MYVAR="hello,goodbye,whatsup"
            }
    
    
    
    
    stages {
        stage('env') {
            when {
               expression { MYVAR ==~ /(.*)goodbye,(.*)/ }
            }
            steps {
                echo "GIT_COMMIT=${GIT_COMMIT}"
                 sh 'printenv'
                echo AN_ACCESS_KEY_USR
               
                echo "user is ${MYVAR}"
                echo env.MYVAR
            }
        }
        stage('gradle') {
            steps {
                sh '''cd untitled; ./gradlew clean build'''
            }
        }
        stage('print1') {
        
            when {
                    expression { params.REQUESTED_ACTION == 'proj1' }
            }
            steps {
                    echo "Hello, bitwiseman!"
            }
        }
        
         stage('print2') {
        
           
            steps {
                    echo PARAM1
                    echo choice2
                    echo params.choice2
                
            }
        }
    }
  
}
