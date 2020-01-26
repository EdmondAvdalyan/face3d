pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')
         
	choice(name: 'CHOICE', choices: ['env1', 'env2', 'env3'], description: 'choice')
	    
        booleanParam(name: 'CHECK', defaultValue: true, description: 'check')
         
	    credentials(
        credentialType: 'com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl',
        defaultValue: 'git',
        description: 'credentials',
        name: 'test_creds',
        required: true
    )
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
	
		    
		    //count repeated string in multiline string  
		    
                script{
			def string = 'some test\nThis is a test text\n'
	                 def count = string.count('test')
			   println('Number of Occurencies:' + count)
                    
		//lines ids with matches
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
			 
			    //name = value
			    
			    def output = ""
			    params.each{name, value ->
	 		     output = output + "$name = $value"
				}
			        writeFile file: 'testfile.txt', text: output
                           
                            //rename filename to filename_new      
			    fileOperations([
				    fileRenameOperation(
					source: "testfile.txt",
					destination: "testfile_new.txt"
				    )
				 ])
			        //archive file_new
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
		stage('WsCleanup') {
            steps {
                step([$class: 'WsCleanup'])
                checkout scm
            }
        }
		}
	post {
    success {
      echo 'HOORRAY!!!'
    }
		failure {
            echo 'CHECK PIPELINE!!!'
        }
  }
	
}
	
		
			


		

        
    
	
