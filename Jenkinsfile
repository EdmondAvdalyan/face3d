pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

  }
    script {
        def s = "IF(AND(x>0,x<100),5,IF(AND(x>101,x<200),6,10))"
        assert 2 == s.count("IF(")
    }
    
        stages {    
        stage('condition ') {
            when {
                expression {
                  
                    return CHECK
                }
            }
            steps {
                echo "MUST BE TRUE"
            }
        } 
     
    
        stage ('params') {
            steps {
                echo "{$params}"
            }
        }
    }
}
