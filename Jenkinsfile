pipeline {
  agent { label 'Java_node' }
  stages {
    stage ('CLONE') {
      steps {
        echo "cloning java project from git"
        sh ''' 
		    git pull https://github.com/arunkumarkp94/Java.git
	   '''
        }
    }
   stage ('BUILD') {
		agent { label 'Java_node' }
		steps {
			echo "Build a binary"
        sh ''' 
			cd ~/jenkins/workspace/Deploy_Java_Build_Tomcat/Java
			mvn clean package
	   '''
      }
    }
	stage ('DEPLOY') {
                steps {
                    script{
                    deploy adapters: [tomcat9(credentialsId: 'tomcat_id', path: '', url: 'http://54.235.43.105:8080/')], contextPath: null, war: '**/*.war'
		    }
                }
 	 }
  }
}
