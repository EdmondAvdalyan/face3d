pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')
        

        choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')

  }
        stages {
       stage('CHECK_condition') {
          input {
                message "Should we continue?"
                ok "Check is Enabled"

               parameters {
                        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')


               }
                }


            steps {
		     echo "${params}"
                script{
			def string = 'some test\nThis is a test text\n'
	                 def count = string.count('test')
			   println('Number of Occurencies:' + count)

			def exp = /(?mi)test/

                           def m = string =~ exp
                              m.eachWithIndex{ match, idx ->
                            println "line[${idx}] = ${match}"

        }
     }
  }
	}

        stage('Check_master') {
            when {
                branch 'master'
            }
            steps {
		    script{
			    def output = ""
			    params.each{name, value ->
	 		     output = output + "$name = $value"
				}
			        writeFile file: 'testfile.txt', text: output
                           


               
			    fileOperations([
				    fileRenameOperation(
					source: "testfile.txt",
					destination: "testfile_new.txt"
				    )
				 ])
			        
			    archiveArtifacts artifacts: 'testfile_new.txt'
			    
	        
				  	 
	 }
                 }
            }
            
		stage("read_file") {
                    steps {
                        script {
                            try {                    
                                env.FILENAME = readFile 'testfile_new.txt'
                                echo "${env.FILENAME}"
                            }
                            catch(Exception e) {
                                 echo 'File not found'
                            }
			}
                        }
		    }
		stage('Git') {
            steps {
                step([$class: 'WsCleanup'])
                checkout scm
            }
        }
		}
	
			}
	
		
			}
		


		

        
    
	
