pipeline{

agent{label 'devslave'}

stages{
stage(scm){
steps{
checkout([$class: 'GitSCM', 
branches: [[name: '*/$branch']], 
userRemoteConfigs: [[credentialsId: 'e9a4298d-cda5-432b-8729-77cff44660ae', url: 'https://github.com/Sindhu-Project/mavenrepo.git']]
])

     }
	     }

stage(sonar){
steps{
withSonarQubeEnv('sonar'){
			
sh 'mvn sonar:sonar'
     			         }
     }
	        }


stage(package){
steps{
sh 'mvn package'
     }
	          }
stage(deploy){
steps{
sh 'mvn deploy'
     }
	         }

stage(tomcat){
steps{
sh 'scp -o "StrictHostKeyChecking no" /root/workspace/Sample/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war 13.233.99.202:/var/lib/tomcat/webapps'
     }
	         }



      }
	  }
