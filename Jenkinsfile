pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

        
    }
    stages {
        stage('Example') {
            steps {
                echo " ${params}"

                echo " ${params.multiline}"

                echo "${params.CHECK}"

                echo "${params.CHOICE}"

                
            }
        }
    }
    stage('condition') {
        steps {
            when {
            
            }
        
        }
    }
}
