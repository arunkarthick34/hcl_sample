node('slave'){
	
   stage('SCM Checkout'){
     git 'https://github.com/arunkarthick34/hcl_sample.git'
   }
		
   stage('Compile-Package'){

	   sh "mvn clean install"
	   sh 'mv target/*.jar target/newapp.war'
	   sh 'cp target/newapp.war /home/newapp.war'
	   
	
	   
	  
   } /*
   stage('SonarQube Analysis') {
	    
	        withSonarQubeEnv('sonar') { 
	          sh "/bin/mvn sonar:sonar"
	        }
	   
	    }
	    */
   stage('Build Docker Imager'){
   sh 'docker build -t arunkarthick34/my_hcl:0.1 .'
   } 
   stage('Docker Image Push'){
   withCredentials([string(credentialsId: 'dockerPass', variable: 'dockerPassword')]) {
   sh "docker login -u arunkarthick34 -p ${dockerPassword}"
    }
   sh 'docker push arunkarthick34/my_hcl:0.1'
   }
/*
   stage('Remove Previous Container'){
	try{
		sh 'docker rm -f tomcattest'
	}catch(error){
		//  do nothing if there is an exception
	}
   stage('Docker deployment'){
   sh 'docker run -d -p 8090:8080 --name tomcattest arunkarthick34/my_hcl:0.1' 
   }
}
	
	*/
	
    
}


