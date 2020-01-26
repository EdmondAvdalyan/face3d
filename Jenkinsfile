pipeline {
    agent any
    parameters {
        string(name: 'TEST', defaultValue: 'test', description: 'test')

        text(name: 'multiline', defaultValue: 'some test\nThis is a test text\n', description: 'multiline text')

        

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
			    params.each{name, value ->
				    def output = "${name} = ${value}"
			     
				}
			    
	writeFile file: "spaon", text: "${output}"
			    
		    }

                 }
            }

        }
    }

