pipeline{
   agent any
   paramerers: {
       booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
   }
   stages{
	stage('test'){
	    parallel{
	         stage('Unit test'){
	             steps{
	                 sh './mvnw test -D testGroups=unit.'
	             }
	         }
	         stage('Integration test'){
	              when{
			  expression {return params.RUN_INTEGRATION_TESTS}
	              }
	              steps{
	                  sh './mvnw test -D testGroups=integration'
	              }
	         }
	    }
	}
   } 
  
}
