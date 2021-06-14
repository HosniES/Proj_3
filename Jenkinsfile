pipeline {	 
    agent { node { label 'maven' } }	 
   	 stages {
     stage("Clean") {
            steps {
                 sh "mvn clean"
            }
         }
   	 stage("Compile") {          	 
   			 steps {               	 
   				 sh "mvn compile"          	 
   			 }     	 
   		 }     	 
   	 stage("Unit test") {          	 
   		 steps {               	 
   				 sh "mvn test"          	 
   			 }     	 
   		 }
     stage("Install") {          	 
   		 steps {               	 
   				 sh "mvn install"          	 
   			 }     	 
   		 }
     }

    	post {
   	 always {
   	 step([$class: 'JacocoPublisher',
   	   	execPattern: 'target/*.exec',
   	   	classPattern: 'target/classes',
   	   	sourcePattern: 'src/main/java',
   	   	exclusionPattern: 'src/test*'
   	 ])
   	 }   
    	}
}
