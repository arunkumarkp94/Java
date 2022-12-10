pipeline{
    agent{
        label 'agent1'
    }
    stages{
        stage('CLONING REPO'){
            steps{
                git branch: 'main', url: 'https://github.com/arunkumarkp94/Java.git'
            }
        }    
            stage('BUILD'){
                steps{
                  sh 'mvn clean install'  
                }
            }
            stage('DEPLOYING'){
                steps{
                     echo "archiving"
                        archiveArtifacts artifacts: '*/*.war', followSymlinks: false
                }
                post{
                    success{
                            deploy adapters: [tomcat9(credentialsId: 'robot', path: '', url: 'http://54.161.203.119:8080/')], contextPath: null, war: '*/*.war'
			    
		    }
                }
            }
        stage ('TESTING') {
		steps {
		sh '''
		cd /opt/jenkins/workspace/Deploy_Java_Build_Tomcat/target
		mvn test
		echo "Testest successfully"
		'''
        	}
		}
    }
}
