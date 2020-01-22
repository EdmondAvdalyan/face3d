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
                
   static void main(String[] args) { 
      String a = "Hello World"; 
		
      // Using public int indexOf(int ch) 
      println(a.indexOf('e')); 
      println(a.indexOf('o')); 
		
      // Using public int indexOf(int ch, int fromIndex) 
      println(a.indexOf('l',1)); 
      println(a.indexOf('e',4));
		
      // Using public int indexOf(string str) 
      println(a.indexOf('el')); 
      println(a.indexOf('or')); 
		
      // Using public int indexOf(string str,int fromIndex) 
      println(a.indexOf('el',1)); 
      println(a.indexOf('or',8)); 
   } 
}
                   
                
            }
           }
        }
     
    }

        

