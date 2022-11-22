pipeline {
  agent { label 'Java_node' }
  stages {
    stage ('CLONE') {
      steps {
        echo "cloning java project from git"
        sh ''' 
		    git clone https://github.com/arunkumarkp94/Java.git
	   '''
        }
    }
   stage ('BUILD') {
		agent { label 'Java_node' }
		steps {
			echo "Build a binary"
        sh ''' 
			mvn clean package
	   '''
      }
    }
	stage ('DEPLOY') {
                steps {
                    script{
                    deploy adapters: [tomcat9(credentialsId: 'e592a559-690e-4edb-8031-245ffc03cf99', path: '', url: 'http://54.235.43.105:8080/')], contextPath: null, war: '**/*.war'
		    }
                }
 	 }
  }
}
