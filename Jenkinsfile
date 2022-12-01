pipeline{
    agent{
        label 'label1'
    }
    stages{
        stage('CLONING REPO'){
            steps{
                git branch: 'main', url: 'https://github.com/cpdani14/Test1_Java.git'
            }
        }    
            stage('BUILD'){
                steps{
                  sh 'mvn clean install'  
                }
            }
            stage('Artifacts_Backup'){
                steps{
                     echo "archiving"
                        archiveArtifacts artifacts: '*/*.war', followSymlinks: false
                }
               
            }
        stage ('TESTING') {
		steps {
		sh '''
			 mvn test
			echo "Testest successfully"
		'''
        	}
		}
    }
}
