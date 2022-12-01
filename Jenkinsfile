pipeline{
    agent{
        label 'label1'
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
                        archiveArtifacts artifacts: '/.war', followSymlinks: false
                }
                post{
                    success{
                        deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://13.233.216.107:8080/')], contextPath: null, war: '*/*.war'

                    }
                }
            }
        stage ('TESTING') {
		steps {
		sh '''
		 cd /opt/jenkins/workspace/Pipeline_Java_Build_Deploy/
		 mvn test
			echo "Testest successfully"
		'''
        	}
		}
    }
}
