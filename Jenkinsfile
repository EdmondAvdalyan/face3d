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
                
    
      def a = "some test\r\nThis is a test text\r\n"; 
		
      def match = a.count('test')  
       def exp = /(?mi)^approved/
def approve = '''approved my signature
Approved new signature
APPROVED old signature
apprOved'''
def m = approve =~ exp
m.eachWithIndex{ match, idx ->
    println "m[${idx}] = ${match}"
}

   
}
                   
                
            }
           }
        }
     
    }

        

