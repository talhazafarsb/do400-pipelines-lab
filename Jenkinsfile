pipeline{
   agent any
   parameters{
       booleanparam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
   }	
	stages{
		stage('test'){
			parallel{
				stage('Unit tests'){
					steps{
					   sh './mvnw test -D testGroups=unit'
					}
				}
				stage('Integration tests'){
					when{
						expression(return params.RUN_INTEGRATION_TESTS )
					}
					steps{
					   sh './mvnw test -D testGroups=integration'
					}
				}
			}
		}
	|	
}
