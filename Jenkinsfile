pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'Who should I say hello to?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'Enter some information about the person')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'Check this value')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'Pick something')

        
    }
    stages {
        stage('Example') {
            steps {
                echo "Hello ${params.TEST}"

                echo "Biography: ${params.multiline}"

                echo "Toggle: ${params.CHECK}"

                echo "Choice: ${params.CHOICE}"

                
            }
        }
    }
}
