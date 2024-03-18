pipeline {
    agent any

	tools {
		maven 'M2_HOME'
	}

	// environment {
	// 	M2_INSTALL = "/home/siddharth/Maven/maven-3.8.1"
	// }

    stages {
		stage('Clone-Repo') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
	    	steps {
				sh 'mvn install -DskipTests'
			}
	    }
		stage('Unit Tests') {
			steps {
				sh 'mvn surefire:test'
			}
		}
		stage('Deployment') {
	    	steps {
				print "Deployment is done!"
				sh 'cp /home/siddharth/.jenkins/workspace/test_pipeline1/target/neeraj.war /home/siddharth/niraj_devops/Neeraj_repo/tools/tomcat/webapps'
				sh  'echo "neeraj war file is dep[loyed on tomacat"'
				sh '/home/siddharth/niraj_devops/Neeraj_repo/tools/tomcat/bin/shutdown.sh'
				sh '/home/siddharth/niraj_devops/Neeraj_repo/tools/tomcat/bin/startup.sh'
				sh  'ls /opt/tomcat/webapps/'
	    	}
		}
    }
}
