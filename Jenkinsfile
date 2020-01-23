pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test?')

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
                script{
                
			def exp = /(?mi)test/
                        def line = '''some test
                                   This is a test text'''
                        def m = line =~ exp
                            m.eachWithIndex{ match, idx ->
                               println "line[${idx}] = ${match}"
	              
		        def count = line.count('test')
	                       println("Number of occurencies is:" + count)
}



   
		}
                   
                
            }
           }
        }
     
    }

        

