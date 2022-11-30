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
			
			mvn clean package
	   '''
      }
    }
	stage ('DEPLOY') {
                steps{
                     echo "archiving"
	sh ''' 	
                       cd /home/ubuntu/jenkins/workspace/Deploy_build/Java/target
			if [ $? -eq 0 ];then
				echo " success "
			else
				echo " fail "
			fi
	   ''' 
                }
 	 }
  }
}
