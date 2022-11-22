pipeline {
  agent { label 'Java_node' }
  stages {
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
                    deploy adapters: [tomcat9(credentialsId: 'e592a559-690e-4edb-8031-245ffc03cf99', path: '', url: 'http://54.235.43.105:8080/')], contextPath: null, war: '**/*.war'
		    }
                }
 	 }
  }
}
