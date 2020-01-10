pipeline {
    agent any
    parameters {
        // Default value here is true.
        booleanParam(name: 'CHECK', defaultValue: true, description: 'This boolean defaults to true!') 
    }
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
            steps {
                echo "MUST BE TRUE"
            } // end of steps
        } // end of stage
    } // end stages
}
