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
  
			String input = "1stline\n2ndLINE\n3rdline";
  			Pattern p = Pattern.compile("(?i)2ndline", Pattern.DOTALL);
			Matcher m = p.matcher(input);
			boolean b = m.find();
			print("match found: " + b);

   
}
                   
                
            }
           }
        }
     
    }

        

