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
                expression {
                  
                    return CHECK
                }
            }
            steps {
                echo "MUST BE TRUE"
            }
        } 
        }  
    node {
    properties([parameters([string(defaultValue: 'ronaldo', description: '', name: 'name', trim: false)])])
   def mvnHome
   stage('Preparation') { // for display purposes
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/linuxacademy/content-cje-prebuild.git']]])
           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Post Job'){
       sh 'bin/makeindex'
   }
   stage('Results') {
      archiveArtifacts 'index.jsp'
   }
}
            
        stage ('params') {
            steps {
                echo "{$params}"
            }
        }
    }
}

