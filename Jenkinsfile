pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

  }
        stages {    
        stage('condition ') {
            when {
          expression { params.CHECK == true} 
            }  
                
            
            steps {
                echo "MUST BE TRUE"
            }
        } 
        
    stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                      booleanParam(name: 'CHECK', defaultValue: true, description: 'check')
                }
            }
            steps {
                echo "Hello, ${CHECK}, nice to meet you."
            }
        }
            
        stage ('params') {
            steps {
                echo "{$params}"
            }
        }
    }
}

