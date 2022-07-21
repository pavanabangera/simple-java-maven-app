pipeline {
  agent { label 'tomcat-slave5' }
	 
	 stages {
	      stage ('git checkout') {
		  parallel {
		        stage ('git checkout1') {
		       steps {
			       git branch: 'master', url: 'https://github.com/pavanabangera/simple-java-maven-app.git' 
				}
			}	
			stage ('git checkout-bitwiseman-patch-1') {
		       steps {
			       git branch: 'bitwiseman-patch-1', url: 'https://github.com/pavanabangera/simple-java-maven-app.git' 
				}
			}	
			}
			}
			stage ('build stage1') {
			    steps {
				     sh 'mvn clean compile'
				}
			}
			stage ('build stage2') { 
			    steps {
				     sh 'mvn clean install'
				}
			}
			stage ('push to artifactory') {
			    steps {
				     sleep 15
				}
			}
			stage ('deploy') {
			    steps {
				     sh 'sudo cp /home/ec2-user/JENKINS1/workspace/jenkinfile/target/*.war /home/ec2-user/apache-tomcat-8.5.81/webapps'
				}
			}
			}
		}	
