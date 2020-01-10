pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

  }
    stages {
          stages {
        stage('parallel-1') {
            when {
                expression {
                    // Given our default value is true, this should 
                    // run if I don't change the parameter from its 
                    // default value of true, to false.
                    return TRUE_OR_FALSE
                }
            }
        }
          }
    }
        stage ('params') {
            steps {
                echo "{$params}"
            }
        }
    
    }
   

