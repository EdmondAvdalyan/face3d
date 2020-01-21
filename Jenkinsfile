pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

    }
        stages {           
      stage('file input') {
  node {
    // Get file using input step, will put it in build directory
    def inputFile = input message: 'Upload file', parameters: [file(name: 'data.txt')]
    // Read contents and write to workspace
    writeFile(file: 'data.txt', text: inputFile.readToString())
    // Stash it for use in a different part of the pipeline
    stash name: 'data', includes: 'data.txt'
  }
}

stage('do something with data') {
  node {
    // Unstash the file into an 'input' directory in the workspace
    dir('input') {
      unstash 'data'
    }
    // do something useful
    sh "ls -lR input/"
  }
}
          stage ('params') {
            steps {
                echo "{$params}"
            }
        }
    }
}


