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
			cd ~/jenkins/workspace/Deploy_build/Java
			mvn clean package
	   '''
      }
    }
	stage ('DEPLOY') {
                steps{
                     echo "archiving"
                        archiveArtifacts artifacts: '/.war', followSymlinks: false
                }
 	 }
  }
}
