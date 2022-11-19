pipeline {
  agent { label 'Java_node' }
  stages {
    stage ('Clone') {
      steps {
        echo "cloning java project from git"
        sh ''' 
		    git clone https://github.com/arunkumarkp94/Java.git
	   '''
        }
    }
   stage ('Build') {
		agent { label 'Java_node' }
		steps {
			echo "Build a binary"
        sh ''' 
			mvn clean package
	   '''
      }
    }
  }
}
